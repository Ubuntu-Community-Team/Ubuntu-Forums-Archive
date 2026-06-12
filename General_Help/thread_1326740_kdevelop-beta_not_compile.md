---
title: "kdevelop-beta not compile"
date: 2009-11-14
forum: General Help
---

### Post by Riot@ct on 2009-11-14
I'm trying to compile and install kdevelop-beta but I get this:
```
$ cmake -DCMAKE_INSTALL_PREFIX=/opt/kdevelop-svn ../                
-- Found Qt-Version 4.5.2 (using /usr/bin/qmake)                                                                                 
-- Found X11: /usr/lib/libX11.so                                                                                                 
-- Phonon Version: 4.3.1                                                                                                         
-- Found KDE 4.3 include dir: /usr/include                                                                                       
-- Found KDE 4.3 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- no apr-config found, subversion support will be disabled
-- no apu-config found, subversion support will be disabled
-- No subversion includes found, subversion support will be disabled
-- No apr includes found, subversion support will be disabled
-- No apu includes found, subversion support will be disabled
-- No subversion client libs found, subversion support will be disabled
-- No subversion repository lib found, subversion support will be disabled
-- No subversion fs lib found, subversion support will be disabled
-- No subversion subr lib found, subversion support will be disabled
-- No subversion wc lib found, subversion support will be disabled
-- No subversion ra lib found, subversion support will be disabled
-- No apr lib found, subversion support will be disabled
-- No apu lib found, subversion support will be disabled

-----------------------------------------------------------------------------
-- The following OPTIONAL packages could NOT be located on your system.
-- Consider installing them to enable more features from this software.
-----------------------------------------------------------------------------
   * Boost (1.35.0 or higher)  <http://www.boost.org>
     Boost libraries for enabling the classbrowser
     The boost libraries are needed to build the Class Browser
   * Subversion (1.3.0 or higher)  <http://subversion.tigris.org>
     Support for Subversion integration
     The subversion libraries are needed for the Subversion support

-----------------------------------------------------------------------------

-- Configuring done
CMake Error in plugins/quickopen/CMakeLists.txt:
  Cannot find source file "expandingdelegate.cpp".  Tried extensions .c .C
  .c++ .cc .cpp .cxx .m .M .mm .h .hh .h++ .hm .hpp .hxx .in .txx


-- Build files have been written to: /home/gp/Workspace/kdevelop-svn/src/kdevplatform/build

```
Can you help me?

---

