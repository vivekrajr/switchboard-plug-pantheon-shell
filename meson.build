project('pantheon-desktop', 'vala', 'c')

gettext_name = meson.project_name() + '-plug'
gnome = import('gnome')
i18n = import('i18n')

add_project_arguments(
    '-DGETTEXT_PACKAGE="@0@"'.format(gettext_name),
    '-DGNOME_DESKTOP_USE_UNSTABLE_API',
    language: 'c'
)

add_project_arguments(
    ['--vapidir', join_paths(meson.current_source_dir(), 'vapi')],
    language: 'vala'
)

plank_dep = dependency('plank', version: '>=0.7.1.1137')
glib_dep = dependency('glib-2.0')
gio_dep = dependency('gio-2.0')
gobject_dep = dependency('gobject-2.0')
gtk_dep = dependency('gtk+-3.0')
posix_dep = meson.get_compiler('vala').find_library('posix')

plug_resources = gnome.compile_resources(
    'plug_resources',
    'data/icons.gresource.xml',
    source_dir: 'data'
)

install_data(
    'data/io.elementary.switchboard.plug.desktop.gschema.xml',
    install_dir: join_paths(get_option('prefix'), get_option('datadir'), 'glib-2.0', 'schemas')
)

subdir('src')
subdir('set-wallpaper-contract')
subdir('po')
