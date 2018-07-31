project(TLMC_gui LANGUAGES CXX)

set(GUI_SOURCES
    DesktopServices.h
    DesktopServices.cpp

    # Icons
    icons/TLMCIcon.h
    icons/TLMCIcon.cpp
    icons/IconList.h
    icons/IconList.cpp

    SkinUtils.cpp
    SkinUtils.h
)
################################ COMPILE ################################

add_library(TLMC_gui SHARED ${GUI_SOURCES})
set_target_properties(TLMC_gui PROPERTIES CXX_VISIBILITY_PRESET hidden VISIBILITY_INLINES_HIDDEN 1)

generate_export_header(TLMC_gui)

# Link
target_link_libraries(TLMC_gui TLMC_iconfix TLMC_logic Qt5::Gui)

# Mark and export headers
target_include_directories(TLMC_gui PUBLIC "${CMAKE_CURRENT_BINARY_DIR}" "${CMAKE_CURRENT_SOURCE_DIR}")

# Install it
install(
    TARGETS TLMC_gui
    RUNTIME DESTINATION ${LIBRARY_DEST_DIR}
    LIBRARY DESTINATION ${LIBRARY_DEST_DIR}
)
