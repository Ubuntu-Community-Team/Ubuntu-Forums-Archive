---
title: "tint2 features"
date: 2012-03-19
forum: General Help
---

### Post by layers on 2012-03-19
I installed tint2, but I cannot see how I can get those 4 icons seen in the image. I don't want to use another dock either. How exactly can I get those 4 application launchers?[IMG]http://img252.imageshack.us/img252/1433/wallpaper2td.jpg[/IMG]

---

### Post by Rodney9 on 2012-03-19
Those are a icon theme, I can't remember it's name.

Good tint2 tutorials - 

[https://code.google.com/p/tint2/wiki/Configure](https://code.google.com/p/tint2/wiki/Configure)

[http://crunchbanglinux.org/forums/topic/16997/how-to-latest-tint2-code-and-new-tint2-additions/](http://crunchbanglinux.org/forums/topic/16997/how-to-latest-tint2-code-and-new-tint2-additions/)

Rodney

---

### Post by mcduck on 2012-03-20
The support for application launchers is currently only in the development version of Tint2 (available from SVN only). So you can't do it yet if you are using Tint2 from Ubuntu's repositories. 

Perhaps there's some PPA with packages compiled from SVN?

---

### Post by layers on 2012-03-24
thanks, I need assistance this is what it says:> To build and install tint2 you need CMake.
These steps should be enough for building tint2:

mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=/usr ../
make
sudo make install

To see additional options you can do after the cmake step a 'cmake -L ../'
 I did this```
svn checkout http://tint2.googlecode.com/svn/trunk/ tint2-read-only
```
then, ```
ibo@ibo-VPCF130FD:~$ cd tint2-read-only/
ibo@ibo-VPCF130FD:~/tint2-read-only$ mkdir build
ibo@ibo-VPCF130FD:~/tint2-read-only$ cd build
```
then ```
ibo@ibo-VPCF130FD:~/tint2-read-only/build$ sudo apt-get install libcairo2-dev libpango1.0-dev libglib2.0-dev libimlib2-dev libxinerama-dev libx11-dev libxdamage-dev libxcomposite-dev libxrender-dev libxrandr-dev
```
and finally ```
ibo@ibo-VPCF130FD:~/tint2-read-only/build$ cmake -DCMAKE_INSTALL_PREFIX=/usr ../
```


i get this:```

ibo@ibo-VPCF130FD:~/tint2-read-only/build$ cmake -DCMAKE_INSTALL_PREFIX=/usr ../
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- checking for modules 'x11;xcomposite;xdamage;xinerama;xrender;xrandr>=1.3'
--   found x11, version 1.4.2
--   found xcomposite, version 0.4.3
--   found xdamage, version 1.1.3
--   found xinerama, version 1.1.1
--   found xrender, version 0.9.6
--   found xrandr, version 1.3.1
-- checking for module 'pangocairo'
--   found pangocairo, version 1.28.4
-- checking for module 'pango'
--   found pango, version 1.28.4
-- checking for module 'cairo'
--   found cairo, version 1.10.2
-- checking for module 'glib-2.0'
--   found glib-2.0, version 2.28.6
-- checking for module 'gobject-2.0'
--   found gobject-2.0, version 2.28.6
-- checking for module 'imlib2>=1.4.2'
--   found imlib2, version 1.4.2
-- Looking for imlib_context_set_display in Imlib2
-- Looking for imlib_context_set_display in Imlib2 - found
-- checking for modules 'x11;xrender'
--   found x11, version 1.4.2
--   found xrender, version 0.9.6
-- checking for module 'gthread-2.0'
--   found gthread-2.0, version 2.28.6
-- checking for module 'gtk+-x11-2.0'
--   package 'gtk+-x11-2.0' not found
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:266 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:320 (_pkg_check_modules_internal)
  src/tint2conf/CMakeLists.txt:10 (pkg_check_modules)


-- Configuring incomplete, errors occurred!
```

the website says it's a working copy, so is there some configuration I am missing somewhere? And I don't understand what the error messages convey...

---

### Post by mcduck on 2012-03-24
```
package 'gtk+-x11-2.0' not found
```
based on this, you haven't installed the dev packages for GTK 2.0

I suppose [libgtk2.0-dev]("apt:libgtk2.0-dev") would be the correct package.

---

### Post by layers on 2012-03-24
alright, that's what it had turned out to be - i didn't know a package was named differently. thanks mcduck.

one last thing - I ran the executable it produced, just to see if it worked, and it placed a second tint2 panel on top of the one I am using currently from sources. In the startup.sh, it is listed as "tint2". How would I list this svn version?

---

### Post by layers on 2012-03-24
i just ran the executable. thanks for a ll the help!

---

