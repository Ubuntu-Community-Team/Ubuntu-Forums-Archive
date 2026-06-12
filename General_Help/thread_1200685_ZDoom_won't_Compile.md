---
title: "ZDoom won't Compile"
date: 2009-06-30
forum: General Help
---

### Post by nickgn12 on 2009-06-30
ive been trying to compile Zdoom following the[ tutorial]("http://zdoom.org/wiki/Compile_ZDoom_on_Linux") at the wiki
it stops at 42% and then it goes on like 
```

[ 42%] Building CXX object src/CMakeFiles/zdoom.dir/m_options.o
/home/nick/Desktop/trunk/src/m_options.cpp: In function ‘void M_OptDrawer()’:
/home/nick/Desktop/trunk/src/m_options.cpp:1717: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:1828: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:1891: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:1898: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:1903: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:1910: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp: In function ‘void M_OptResponder(event_t*)’:
/home/nick/Desktop/trunk/src/m_options.cpp:2343: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2346: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2353: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2358: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2374: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2378: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2399: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2419: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2477: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2478: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2549: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2552: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2559: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2564: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2580: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2584: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2605: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2625: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2683: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2684: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2842: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:2843: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp: In function ‘void UpdateJoystickMenu(IJoystickConfig*)’:
/home/nick/Desktop/trunk/src/m_options.cpp:3112: error: ‘I_GetJoysticks’ was not declared in this scope
/home/nick/Desktop/trunk/src/m_options.cpp:3161: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:3167: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_options.cpp:3174: error: invalid use of incomplete type ‘struct IJoystickConfig’
/home/nick/Desktop/trunk/src/m_menu.h:121: error: forward declaration of ‘struct IJoystickConfig’
make[2]: *** [src/CMakeFiles/zdoom.dir/m_options.o] Error 1
make[1]: *** [src/CMakeFiles/zdoom.dir/all] Error 2
make: *** [all] Error 2
```for a while
all i know is that it's something about joysticks :confused:
can anyone help me?

---

### Post by ivangotoy on 2009-06-30
Hope this helps a little.
[http://forum.zdoom.org/viewtopic.php?f=2&t=22589](http://forum.zdoom.org/viewtopic.php?f=2&t=22589)

---

