project(tcod)

cmake_minimum_required(VERSION 2.8)

set(tcod_files
  src/path_c.c
  src/gui/widget.cpp
  src/gui/label.cpp
  src/gui/hbox.cpp
  src/gui/toolbar.cpp
  src/gui/togglebutton.cpp
  src/gui/statusbar.cpp
  src/gui/image.cpp
  src/gui/radiobutton.cpp
  src/gui/textbox.cpp
  src/gui/flatlist.cpp
  src/gui/vbox.cpp
  src/gui/container.cpp
  src/gui/button.cpp
  src/gui/slider.cpp
  src/txtfield_c.c
  src/mersenne.cpp
  src/namegen_c.c
  src/parser.cpp
  src/noise.cpp
  src/sys_c.c
  src/fov_permissive.c
  src/mouse.cpp
  src/bsp_c.c
  src/namegen.cpp
  src/image_c.c
  src/sys_sdl_img_png.c
  src/mersenne_c.c
  src/fov_permissive2.c
  src/fov_restrictive.c
  src/txtfield.cpp
  src/noise_c.c
  src/path.cpp
  src/color.cpp
  src/sys_sdl_img_bmp.c
  src/tree_c.c
  src/zip.cpp
  src/wrappers.c
  src/fov.cpp
  src/list_c.c
  src/heightmap.cpp
  src/image.cpp
  src/color_c.c
  src/fov_c.c
  src/heightmap_c.c
  src/fov_circular_raycasting.c
  src/png/lodepng.c
  src/sys_opengl_c.c
  src/console.cpp
  src/fov_digital.c
  src/lex_c.c
  src/console_c.c
#  src/sys_sfml_c.c
  src/bresenham.cpp
  src/lex.cpp
  src/fov_diamond_raycasting.c
  src/zip_c.c
  src/parser_c.c
  src/bresenham_c.c
  src/fov_recursive_shadowcasting.c
  src/bsp.cpp
  src/sys.cpp
  src/sys_sdl_c.c
)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include/gui)

add_library(tcod SHARED ${tcod_files})

find_package(SDL REQUIRED)
target_include_directories(tcod PRIVATE ${SDL_INCLUDE_DIR})
target_link_libraries(tcod ${SDL_LIBRARY})

find_package(SDL_image REQUIRED)
target_include_directories(tcod PRIVATE ${SDL_IMAGE_INCLUDE_DIRS})
target_link_libraries(tcod ${SDL_IMAGE_LIBRARIES})

find_package(OpenGL REQUIRED)
target_include_directories(tcod PRIVATE ${OPENGL_INCLUDE_DIR})
target_link_libraries(tcod ${OPENGL_LIBRARIES})

find_package(ZLIB REQUIRED)
target_include_directories(tcod PRIVATE ${ZLIB_INCLUDE_DIRS})
target_link_libraries(tcod ${ZLIB_LIBRARIES})

target_link_libraries(tcod dl)

set_target_properties (tcod PROPERTIES LINK_FLAGS "-Wl,--no-undefined")
