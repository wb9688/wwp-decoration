project(
    'wwp-decoration',
    'c',
    'cpp',
    version: '0.1.0',
    license: 'MIT',
    meson_version: '>=0.51.0',
    default_options: [
        'cpp_std=c++17',
        'c_std=c11',
        'warning_level=2',
        'werror=false',
    ],
)

wayfire = dependency('wayfire')
wlroots = dependency('wlroots')
pixman = dependency('pixman-1')
wfconfig = dependency('wf-config')
cairo = dependency('cairo')
pango = dependency('pango')
pangocairo = dependency('pangocairo')

add_project_arguments(['-DWLR_USE_UNSTABLE'], language: ['cpp', 'c'])
add_project_arguments(['-DWAYFIRE_PLUGIN'], language: ['cpp', 'c'])
add_project_link_arguments(['-rdynamic'], language:'cpp')

add_project_arguments(['-Wno-unused-parameter'], language: 'cpp')

wwp_switcher = shared_module('wwp-decoration', [
        'decoration.cpp',
        'deco-subsurface.cpp',
        'deco-button.cpp',
        'deco-layout.cpp',
        'deco-theme.cpp'
    ],
    dependencies: [wayfire, wlroots, pixman, wfconfig, cairo, pango, pangocairo],
    install: true, install_dir: join_paths(get_option('libdir'), 'wayfire'))

install_data('wwp-decoration.xml', install_dir: wayfire.get_variable(pkgconfig: 'metadatadir'))
