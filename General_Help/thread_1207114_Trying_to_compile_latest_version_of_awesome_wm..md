---
title: "Trying to compile latest version of awesome wm."
date: 2009-07-07
forum: General Help
---

### Post by dragos240 on 2009-07-07
Hi, I am trying to compile the latest version of awesome, but errors occur,

```

$ make
Running cmake…
-- cat -> /bin/cat
-- ln -> /bin/ln
-- grep -> /bin/grep
-- git not found.
-- hostname -> /bin/hostname
-- gperf -> /usr/bin/gperf
-- asciidoc not found.
-- xmlto not found.
-- gzip -> /bin/gzip
-- lua -> /usr/bin/lua
-- luadoc not found.
-- convert -> /usr/bin/convert
-- Looking for doxygen...
-- Looking for doxygen... - NOT found
-- Looking for dot tool...
-- Looking for dot tool... - NOT found
-- Could NOT find Lua51  (missing:  LUA_LIBRARIES LUA_INCLUDE_DIR)
-- Not generating manpages. Missing: asciidoc xmlto
-- Not generating luadoc. Missing: luadoc
-- checking for modules 'glib-2.0;cairo;x11;pango>=1.19.3;pangocairo>=1.19.3;xcb-randr;xcb-xtest;xcb-xinerama;xcb-event>=0.3.4;xcb-aux>=0.3.0;xcb-atom>=0.3.0;xcb-keysyms>=0.3.4;xcb-icccm>=0.3.3;xcb-image>=0.3.0;xcb-property>=0.3.0;cairo-xcb;libstartup-notification-1.0>=0.10;xproto>=7.0.15;imlib2;libxdg-basedir>=1.0.0'
--   package 'xcb-randr' not found
--   package 'xcb-xinerama' not found
--   package 'xcb-event>=0.3.4' not found
--   package 'xcb-aux>=0.3.0' not found
--   package 'xcb-atom>=0.3.0' not found
--   package 'xcb-keysyms>=0.3.4' not found
--   package 'xcb-icccm>=0.3.3' not found
--   package 'xcb-image>=0.3.0' not found
--   package 'xcb-property>=0.3.0' not found
--   package 'libstartup-notification-1.0>=0.10' not found
--   package 'xproto>=7.0.15' not found
--   package 'imlib2' not found
--   package 'libxdg-basedir>=1.0.0' not found
CMake Error at /usr/share/cmake-2.6/Modules/FindPkgConfig.cmake:270 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.6/Modules/FindPkgConfig.cmake:322 (_pkg_check_modules_internal)
  awesomeConfig.cmake:134 (pkg_check_modules)
  CMakeLists.txt:15 (include)


CMake Error at awesomeConfig.cmake:157 (message):
Call Stack (most recent call first):
  CMakeLists.txt:15 (include)


-- Configuring incomplete, errors occurred!
make: *** [cmake] Error 1

```

---

### Post by mc4man on 2009-07-08
well it's showing you what's needed. Note that some of those packages are not available for jaunty but are for karmic. (you can if you wish probably install them - mainly libxcb packages and the -devs.  

The karmic build-deps for awesome 3.3.1 (red are karmic packages, if installing  the -dev, the 'regular package must also be installed first or at same time

> Build-Depends: cdbs, debhelper (>= 5), libcairo2-dev, xmlto, asciidoc, libpango1.0-dev, cmake (>= 2.6.0), gperf, lua5.1, luadoc (>= 3.0.1), libxcb-xtest0-dev, [COLOR="Red"]libxcb-icccm1-dev[/COLOR] (>= 0.3.3), [COLOR="Red"]libxcb-event1-dev [/COLOR](>= 0.3.0), libxcb-randr0-dev (>= 0.3.0), [COLOR="Red"]libxcb-aux0-dev[/COLOR] (>= 0.3.0), libxcb-keysyms1-dev (>= 0.3.4), libxcb-xinerama0-dev, [COLOR="Red"]libxcb-atom1-dev[/COLOR] (>= 0.3.0), libxcb-image0-dev (>= 0.3.0), libev-dev, liblua5.1-dev, libimlib2-dev, libdbus-1-dev, libxdg-basedir-dev (>= 1.0.0), libstartup-notification0-dev (>= 0.10), imagemagick



libxcb-keysyms-dev is available in jaunty and suitable (vs. libxcb-keysyms[COLOR="Red"]1[/COLOR]-dev
[COLOR="Red"]libxcb-property1[/COLOR] may or may not be needed for running

You may also want to install doxygen (jaunty version

There is an version available in jaunty though older and not using libxcb libraries (which to some extent are considered 'experimental'

---

