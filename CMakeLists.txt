cmake_minimum_required( VERSION 3.10 FATAL_ERROR )

project( kicad-template-jlcpcb NONE )

#================================================
# Locations for install targets.
#================================================
set( KICAD_USER_DATAS $ENV{HOME}/.local/share/kicad)
file (GLOB KICAD_USER_DATA_FILES "${KICAD_USER_DATAS}/*")

#================================================
# Installed files.
#================================================

# Select project template directories
file (GLOB PROJECT_DIRS "Projects/*")

foreach( file ${KICAD_USER_DATA_FILES} )
    message( STATUS "KiCad user data file: ${file}/template" )
    # Copy them to destination
    foreach( tpl ${PROJECT_DIRS} )
        install( DIRECTORY ${tpl} DESTINATION ${file}/template COMPONENT resources )
    endforeach()
    
endforeach( file ${KICAD_USER_DATA_FILES} )

