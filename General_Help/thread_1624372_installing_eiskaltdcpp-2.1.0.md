---
title: "installing eiskaltdcpp-2.1.0"
date: 2010-11-17
forum: General Help
---

### Post by RastaManPower on 2010-11-17
can anyone explain to me how to install this?
i unzipped the package and found the install instrucitons but i dont understand how to install it. this is what it says:
*******************************************************************************
Program Depends
*******************************************************************************
--------
:common:
--------
bzip2
zlib
iconv (libc on GNU/Linux)
----------------
:libeiskaltdcpp:
----------------
gettext
libssl (>= 0.9.8)
liblua5.1 (optional, see cmake keys)
----------------
:eiskaltdcpp-qt:
----------------
libqtcore4, libqtgui4, libqt4-network, libqt4-xml (>= 4.4.0)
libqt4-script (>= 4.4.0) (optional, see cmake keys)
libqt4-dbus (>= 4.4.0) (optional, see cmake keys)
libaspell (optional, see cmake keys)
-----------------
:eiskaltdcpp-gtk:
-----------------
gettext
libpango
libgtk2 (>= 2.10)
libglib2 (>= 2.10)
libglade2 (>= 2.4)
libnotify (>= 0.4.1)
libgnome2 (optional, see cmake keys)
miniupnpc (optional, see cmake keys)


*******************************************************************************
Opional Depends
*******************************************************************************
----------------
:eiskaltdcpp-qt:
----------------
sh (bash, dash, etc...)
    see examples/ and eiskaltdcpp-qt/qtscripts/
php5-cli (or other version, check the compatibility by yourself)
    see eiskaltdcpp-qt/examples/ and eiskaltdcpp-qt/qtscripts/
libqtscript4-core, libqtscript4-gui, libqtscript4-network, libqtscript4-xml
    see eiskaltdcpp-qt/qtscripts/
-----------------
:eiskaltdcpp-gtk:
-----------------
...


*******************************************************************************
Build Depends
*******************************************************************************
--------
:common:
--------
gcc
zlib
bzip2
cmake (>= 2.6.0)
iconv (libc on GNU/Linux)
pkg-config
----------------
:libeiskaltdcpp:
----------------
gettext
libboost-dev (headers only) (optional, see cmake keys)
liblua5.1-dev (optional, see cmake keys)
----------------
:eiskaltdcpp-qt:
----------------
qt4 (>=4.4.0)
libaspell-dev (optional, see cmake keys)
-----------------
:eiskaltdcpp-gtk:
-----------------
libgtk2.0-dev
libglade2-dev
libnotify-dev
libgnome2-dev (optional, see cmake keys)
miniupnpc (optional, see cmake keys)


*******************************************************************************
Installation in Linux and other UNIX-like systems
*******************************************************************************
mkdir -p builddir && cd builddir
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr ../
make -j2
sudo make install

---------
# Note: you can get the lastest program sorces from subversion
svn export [http://eiskaltdc.googlecode.com/svn/branches/trunk/](http://eiskaltdc.googlecode.com/svn/branches/trunk/) eiskaltdcpp-trunk


*******************************************************************************
Keys for cmake
*******************************************************************************
----------------
:libeiskaltdcpp:
----------------
-DLOCAL_BOOST=ON/OFF (default: OFF)
    use local boost headers
-DLUA_SCRIPT=ON/OFF (default: OFF)
    lua scripts
----------------
:eiskaltdcpp-qt:
----------------
-DUSE_QT=ON/OFF (default: ON)
    build EiskaltDC++ with Qt interface
-DUSE_ASPELL=ON/OFF (default: not set)
    forced use or not use aspell
-DFREE_SPACE_BAR_C=ON/OFF (default: ON)
    free space bar in status panel
-DDBUS_NOTIFY=ON/OFF (default: ON)
    use or not use QtDBus module
-DUSE_JS=ON/OFF (default: OFF)
    Enable/disable QtScript basic support
-DUSE_QT_QML=ON/OFF (default: OFF)
    Enable/disable Qt Declarative Ui support. Work only with Qt >= 4.7.0
-DUSE_ICON_THEME=ON/OFF (default: OFF)
    Using system icon theme. Work only with Qt >= 4.6.0 and only in KDE and Gnome.
-----------------
:eiskaltdcpp-gtk:
-----------------
-DUSE_GTK=ON/OFF (default: OFF)
    build EiskaltDC++ with Gtk interface (based on FreeDC++ and LinuxDC++)
-DUSE_LIBGNOME2=ON/OFF (default: OFF)
    Enable/disable sound notifications support in EiskaltDC++ Gtk
-DUSE_LIBNOTIFY=ON/OFF (default: ON)
    Enable/disable popup notifications support in EiskaltDC++ Gtk
--------
:common:
--------
-DWITH_EMOTICONS=ON/OFF (default: ON)
    If ON install emoticons/
-DWITH_EXAMPLES=ON/OFF (default: ON)
    If ON install examples/
-DWITH_LUASCRIPTS=ON/OFF (default: OFF)
    If ON install luascripts/
-DUSE_MINIUPNP=ON/OFF (default: ON)
    use or not use miniupnpc lib
-DLOCAL_MINIUPNP=ON/OFF (default: OFF)
    If ON use local miniupnpc lib (not set this in ON if you not set USE_MINIUPNP in ON)
-DWITH_SOUNDS=ON/OFF (default: OFF)
    If ON install sounds/
-Dlinguas:STRING="needed translations, separator is whitespace" (default: *)
    examples:
    -Dlinguas="en ru" - install ru and en translations
    -Dlingaus="*"     - install all translations
    -Dlinguas=""      - don't install any translation
-DFORCE_XDG=ON/OFF (default: ON)
    use or not use $XDG_CONFIG_HOME and $XDG_CONFIG_DOWNLOADS variables
    see [http://standards.freedesktop.org/basedir-spec/latest/ar01s03.html](http://standards.freedesktop.org/basedir-spec/latest/ar01s03.html)
-DCMAKE_INSTALL_PREFIX=<prefix for install> (default: /usr/local)
    .
-DLIBDIR=<lib prefix> (default: lib)
    install lib in <prefix for install>/<lib prefix>
    examples:
    -DLIBDIR=lib64 - install lib in <prefix for install>/lib64
-DLIB_INSTALL_DIR=<lib prefix> (default: lib)
    see -DLIBDIR
-DESKTOP_ENTRY_PATH=<prefix for install> (default: /usr/local/share/applications/)
    .
-PIXMAPS_ENTRY_PATH=<prefix for install> (default: /usr/local/share/pixmaps/)
    .
-DCMAKE_BUILD_TYPE={Release, RelWithDebInfo, Debug, MinRelSize}
    .
And other standart cmake keys...

---------
# Example of the complete assembly:
mkdir -p builddir && cd builddir
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr -DUSE_QT=ON -DUSE_GTK=ON -DUSE_JS=ON -DUSE_ASPELL=ON -DFREE_SPACE_BAR_C=ON  -DCREATE_MO=ON -DLUA_SCRIPT=ON -DWITH_SOUNDS=ON -DWITH_LUASCRIPTS=ON -DUSE_MINIUPNP=ON -DLOCAL_MINIUPNP=ON ../
make
sudo make install


*******************************************************************************
Uninstall program
*******************************************************************************
sudo make uninstall


*******************************************************************************
*BSD specific notes
*******************************************************************************
mkdir -p builddir && cd builddir
cmake -DCMAKE_BUILD_TYPE=Release ../
gmake -j2
sudo gmake install


*******************************************************************************
Mac OS X specific notes
*******************************************************************************
# For generate native bundle on Mac OS X use:
cpack -G DragNDrop


*******************************************************************************
MS Windows specific notes
*******************************************************************************
Instructions are available in the file: win32/READ_ME.txt


__________________________________________________________________
 Example of the complete assembly:
mkdir -p builddir && cd builddir
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr -DUSE_QT=ON -DUSE_GTK=ON -DUSE_JS=ON -DUSE_ASPELL=ON -DFREE_SPACE_BAR_C=ON  -DCREATE_MO=ON -DLUA_SCRIPT=ON -DWITH_SOUNDS=ON -DWITH_LUASCRIPTS=ON -DUSE_MINIUPNP=ON -DLOCAL_MINIUPNP=ON ../
make
sudo make install

i am getting this error
nico@nico:~/eiskalt$ cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr -DUSE_QT=ON -DUSE_GTK=ON -DUSE_JS=ON -DUSE_ASPELL=ON -DFREE_SPACE_BAR_C=ON  -DCREATE_MO=ON -DLUA_SCRIPT=ON -DWITH_SOUNDS=ON -DWITH_LUASCRIPTS=ON -DUSE_MINIUPNP=ON -DLOCAL_MINIUPNP=ON ../
CMake Error: The source directory "/home/nico" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.
nico@nico:~/eiskalt$ cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr -DUSE_QT=ON -DUSE_GTK=ON -DUSE_JS=ON -DUSE_ASPELL=ON -DFREE_SPACE_BAR_C=ON  -DCREATE_MO=ON -DLUA_SCRIPT=ON -DWITH_SOUNDS=ON -DWITH_LUASCRIPTS=ON -DUSE_MINIUPNP=ON -DLOCAL_MINIUPNP=ON ../eiskalt
-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:70 (MESSAGE):
  Could NOT find BZip2 (missing: BZIP2_LIBRARIES BZIP2_INCLUDE_DIR)
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindBZip2.cmake:30 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:64 (find_package)


-- Configuring incomplete, errors occurred!

---

### Post by pavelvat on 2010-11-18
Information from official site [http://code.google.com/p/eiskaltdc/](http://code.google.com/p/eiskaltdc/) 

> Now eiskaltdcpp package is available in official Debian >= 6.0 (Squeeze) and Ubuntu >= 10.10 (Maverick Meerkat) repositories.  

eiskaltdcpp-unstable (daily builds) and eiskaltdcpp packages for Debian GNU/Linux version >= 6.0 (Squeeze) and for Ubuntu version >= 9.04 (Jaunty Jackalope) can be found here (see maintainer notes). Unofficial packages for Debian (squeeze, sid) and Ubuntu (jaunty, karmic, lucid, maverick) are also available here 

---

### Post by RastaManPower on 2010-11-18
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
MINIUPNP_INCLUDE_DIR (ADVANCED)
   used as include directory in directory /home/nico/Desktop/eis/extra

-- Configuring incomplete, errors occurred!
how i fic this error?

---

### Post by RastaManPower on 2010-11-18
upnp (headers){miniupnpc}:/usr/lib/libminiupnpc.a (MINIUPNP_INCLUDE_DIR-NOTFOUND)

---

### Post by pavelvat on 2010-11-18
Why build from source when there is a pre-compiled packages?
[https://launchpad.net/~tehnick/+archive/tehnick/+packages](https://launchpad.net/~tehnick/+archive/tehnick/+packages)

upnp:
Try to delete everything in the builddir directory and repeat all over again.

---

### Post by RastaManPower on 2010-11-18
libminiupnpc.so.5
^ i think i am missing this but cant find on the net

---

### Post by RastaManPower on 2010-11-18
i tryed the deb from the site u gave me but it gives me error
Dependency is not satisfiable: libeiskaltdcpp2.1.x (= 2.1.0-1ppa1~maverick1)

---

### Post by pavelvat on 2010-11-19
> **RastaManPower said:**
> libminiupnpc.so.5
^ i think i am missing this but cant find on the net

 source miniupnpc are in eiskaltdcpp-2.1.0.tar.bz2 if cmake-flags -DUSE_MINIUPNP=ON -DLOCAL_MINIUPNP=ON were raised will be used by a local copy miniupnpc of eiskaltdcpp-2.1.0.tar.bz2

---

### Post by pavelvat on 2010-11-19
> **RastaManPower said:**
> i tryed the deb from the site u gave me but it gives me error
 Dependency is not satisfiable: libeiskaltdcpp2.1.x (= 2.1.0-1ppa1~maverick1)

russian:
[http://tehnick-8.narod.ru/eiskaltdcpp/](http://tehnick-8.narod.ru/eiskaltdcpp/)

english translate:
[http://translate.google.com/translate?hl=ru&sl=ru&tl=en&u=http://tehnick-8.narod.ru/eiskaltdcpp/](http://translate.google.com/translate?hl=ru&sl=ru&tl=en&u=http://tehnick-8.narod.ru/eiskaltdcpp/)

```
sudo add-apt-repository ppa:tehnick/tehnick
sudo apt-get update
sudo apt-get install eiskaltdcpp

```  or  ```
sudo add-apt-repository ppa:tehnick/tehnick
sudo apt-get update
sudo apt-get install eiskaltdcpp-qt
sudo apt-get install eiskaltdcpp-emoticons eiskaltdcpp-scripts eiskaltdcpp-sounds

```  or  ```
sudo add-apt-repository ppa:tehnick/tehnick
sudo apt-get update
sudo apt-get install eiskaltdcpp-gtk
sudo apt-get install eiskaltdcpp-emoticons eiskaltdcpp-scripts eiskaltdcpp-sounds

```

---

