project('liftoff', 'cpp',
  default_options : 'cpp_std=c++11')

lo_libs = subproject('lo_libs')

#subprojects = lo_libs.get_variable('subprojects')

foreach s : subprojects
    dep = s + '_dep'
    set_variable(dep, subproject(s).get_variable(dep))
endforeach

shuttlelib = static_library('lo_shuttle', 'lo_shuttle.cpp',
  dependencies : [lo_strings_dep, lo_adder_dep])

test('shuttle countdown', executable('countdown', 'shuttletest.cpp', link_with : shuttlelib,
    dependencies : [lo_test_dep]))

executable('shuttle_launcher', 'main.cpp',
  link_with : shuttlelib)

