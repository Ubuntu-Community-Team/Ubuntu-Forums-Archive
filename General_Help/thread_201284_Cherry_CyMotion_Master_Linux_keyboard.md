---
title: "Cherry CyMotion Master Linux keyboard"
date: 2006-06-21
forum: General Help
---

### Post by KimJarvis on 2006-06-21
I bought a Cherry Cymotion Master Linux keyboard.  The instructions ask the user to build their own debian package and re build the kernel!!!!  

I am reminded of why casual open office users like myself should stick to windows platform.  This supposedly linux keyboard took less than 2 minutes to install on windows.

The installation CD contains the keyman application to manage the keyboard.  The debian package is compiled for i386.  I am using the amd64 bit version of ubuntu 6.06.  There are source files for building the application.  The instructions are included below, I didn't get very far, apparently KDE development files are requried.  

The CD also contains a readme file with instructions on patching the linux-kernel. The first line of which asks the user to change directory to a directory that does not exist in my installation.  The instructions are included below.



Copyright (c) 2005 CHERRY GMBH

Readme

30/11/2005

******************************





Table of Contents

=================

1. User management

2. Patching the Linux-kernel

3. Version collisions

4. Known Bug list





1. User management

------------------

Users who are using the KeyMan-software must be a member of the 

group 'keyman'.

Adding the user test to the group keyman:

"usermod -A keyman test"





2. Patching the Linux-kernel

----------------------------

To use all additional keys of the Cherry-keyboard you have carry out an 

update of the kernel.



2.1 Run the kernel-patch

~~~~~~~~~~~~~~~~~~~~~~~~

Change directory:

cd /usr/src/linux/drivers/usb/input/



Rebuild hid-input.c:

patch hid-input.c ~USERNAME/keyman/kernel/hid-input.c.diff



Rebuild hid-core.c:

patch hid-core.c ~USERNAME/keyman/kernel/hid-core.c.diff



3.2 Compiling a new kernel

~~~~~~~~~~~~~~~~~~~~~~~~~~

Go as root to the source-directory of the kernel:

cd /usr/src/linux/



Call the configuration-tool for modules of the new kernel:

"make xconfig"



Modules which are absolutely necessary for starting the system, must be 

bounded to the kernel by assigning them with a check mark. Modules that 

are not required for booting can also be loaded later (mark those with 

a dot).

Note: all settings are depending upon the hardware of your system.



Important modules are: (in case of availability on the system)

- Filesystem (e. g. Ext3) support

- ATA/ATAPI support

- SCSI device support



After finishing the configuration save and close the tool.

Then run the commands in the following sequence:

1) make

2) make modules

3) make modules_install

4) make bzImage



Your new kernel is now ready and saved at: 

/usr/src/linux/arch/i386/boot/bzImage



If the bootloader "grub" is installed open /boot/grub/menu.lst with an 

editor (e.g. vi) and add a new starting-option:

"vi /boot/grub/menu.lst"



Create a copy of the entry from the old kernel with a different name and 

change the kernel-path to:

/usr/src/linux/arch/i368/boot/bzImage



Now you can perform a reboot. On starting up, the new kernel can be chosen.





3. KnownBug list

----------------

3.1 KeyMan-key doesn't work on PS/2

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

It's recommended to use the USB port on keyboards which can be connected 

via USB and PS/2. If you connect the keyboard on PS/2 the KeyMan-key 

doesn't work, so the function 'KeyMan + Additional Key' isn't available.



and...


Table of Contents
=================

1.   Requirements
1.1  Software when using the daemon
1.2  Software needed to compile
1.3  How to build
1.4  Build Problems
2.   Installation
3.   Running
3.1  Systray program
3.2  Daemon
4.   Problems
4.1. "Daemon already running"
4.2. Crashes
4.3. USB
4.4. Some keys don't work for a user


1. Requirements
===============

1.1 Software when using the daemon
----------------------------------
* aumix
* eject
* evolution
* kcalc
* konqueror
* xmms
+ other software for which keyman is preconfigured for

1.2 Software needed to compile
------------------------------
* make
* gcc (the compiler collection)
* X11 development files
* QT (threaded version) + development files
* kde + development files
* libtool
* xerces + development files
* kernel header files (for inputdev plugin and input tunnel)
  (usually installed under /usr/include/linux)

1.3 How to build
------------------
Configure project
  ./configure
Build project
  make
Build binary archive package
  make package_bin
Build deb (Debian) package
  * debian packages are build from a clean tree
  * become root (su or sudo or whatever you like)
    ./debian/rules binary
  * the result is a debian package in the folder above the source folder
Build rpm (SuSE) package
  make package_rpm
Build source archive
  make package_src

All packages are built in the directory above the top level directory except
the rpm package which can be found in /usr/src/packages/RPMS/<arch> where
"<arch>" is something like "i586" (look at the output when building).


1.4 Build Problems
------------------
SuSE 9.1 ships a version of make that is not fully functional (GNU make version
3.80 has bugs which are known). In any case try an online update.
If you get "missing separator":
  Make tries to re-configure the package because some *.in files have
  changed. In that case just run "./configure" in the top-level directory.
If you get "memory exhausted":
   Download the latest cvs version.
      (It makes me wonder BTW why it did work on the other SuSE9.1 installation
       - maybe they fixed that problem by using the online update/patching
       system)
	In general this shouldn't happen as a workaround is integrated in the
   respective Makefiles.


2. Installation
===============
see INSTALL


3. Running
==========

3.1 Systray program
-------------------
Start systray program
   If you have installed the package a KDE-Menu Entry should have been created.
   Start the systray Application by selecting the "Keyman" entry.
   Otherwise run it manually by executing "kkeymansystray".
   The systray program takes care of starting the daemon automagically.


3.2 Server
----------
start server program
	a) with default (configurated) plugin
      * keymanserver
   b) with kde gui plugin
      * keymanserver --plugin /usr/share/keyman/plugins/kde-gui.so
   c) with console plugin
      * keymanserver --plugin /usr/share/cherry/plugins/console.so
To end the server
   press control+c (in case of the console plugin)
or type
	keymanserver --quit (console or kde-gui)


4. Problems
===========

4.1. "Server already running"
-----------------------------
If you see a message saying that the daemon is already running although the
daemon is actually not running, delete the file "/tmp/KeymanSocket_<UserName>".

4.2. Crashes
------------
If you installed the binary version and you get crashes, then this might be
due to differences in the installed packages on the build machine and your
machine. In this case try building from source.

4.3. USB
--------
If you want to use the additional keys of your CyMotion Linux keyboard with
USB, you have to recompile the kernel-module "hid".
For further instructions on how to recompile parts of your kernel, please see
documentation included in your distribution or visit [www.kernel.org](www.kernel.org)
Apply cymolin/kernel/drivers/usb/input/hid-input.c.diff to
/usr/src/linux/drivers/usb/input/hid-input.c before compiling.

Example:
cd /usr/src/linux/drivers/usb/input
patch hid-input.c < $HOME/cymolin/kernel/hid-input.c.diff

If you want to use a "normal" CyMotion Master Solar or a
CyMotion Master XPress, you also have to apply
cymolin/kernel/drivers/usb/input/hid-core.c.diff

And don't forget to copy your changed hid-module to the appropriate
location and do a "rmmod hid" and a "modprobe hid" or simply
reboot your system

4.4. Some keys don't work for a user
------------------------------------
* check wether the keys are configured correctly
* check wether the user is in the group "keyman"

---

### Post by KimJarvis on 2006-06-21
This is my attempt to build the keyman application for AMD64.  I copied the linux directory from the CD.  Then attempted to run configure.  None of the prerequisite software, compilers etc. seems to be installed.

kim@shuttle:~/linux$ cd keyman
kim@shuttle:~/linux/keyman$ ls
config              install              make_rpm_mandrake.sh
configure           isetkeycode          make_rpm.sh
configure_gnome.sh  kernel               make_rpm_suse10.sh
configure.in        keymanconfiguration  make_rpm_suse_9.2.sh
configure_kde.sh    kkeymanconfig        readme
debian              ksystray             rpm
doc                 labelitems.txt       scripts
etc                 library              server
gkeymanconfig       license              setkeymanscancode
gsystray            Makefile.in          shared
icons               makelabel.vbs        test
inputtunnel         make_rpm_fedora.sh   xkbdstatus
kim@shuttle:~/linux/keyman$ ./configure
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
kim@shuttle:~/linux/keyman$ ls
config              install               make_rpm.sh
config.log          isetkeycode           make_rpm_suse10.sh
configure           kernel                make_rpm_suse_9.2.sh
configure_gnome.sh  keymanconfiguration   readme
configure.in        kkeymanconfig         rpm
configure_kde.sh    ksystray              scripts
debian              labelitems.txt        server
doc                 library               setkeymanscancode
etc                 license               shared
gkeymanconfig       Makefile.in           test
gsystray            makelabel.vbs         xkbdstatus
icons               make_rpm_fedora.sh
inputtunnel         make_rpm_mandrake.sh
kim@shuttle:~/linux/keyman$ make
bash: make: command not found
kim@shuttle:~/linux/keyman$ cat config.log
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by Cherry Keyboard Tools configure 1.0.0-1, which was
generated by GNU Autoconf 2.59.  Invocation command line was

  $ ./configure

## --------- ##
## Platform. ##
## --------- ##

hostname = shuttle
uname -m = x86_64
uname -r = 2.6.15-25-amd64-generic
uname -s = Linux
uname -v = #1 SMP PREEMPT Wed Jun 14 11:28:03 UTC 2006

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = x86_64
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/bin/X11
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1328: checking for g++
configure:1357: result: no
configure:1328: checking for c++
configure:1357: result: no
configure:1328: checking for gpp
configure:1357: result: no
configure:1328: checking for aCC
configure:1357: result: no
configure:1328: checking for CC
configure:1357: result: no
configure:1328: checking for cxx
configure:1357: result: no
configure:1328: checking for cc++
configure:1357: result: no
configure:1328: checking for cl
configure:1357: result: no
configure:1328: checking for FCC
configure:1357: result: no
configure:1328: checking for KCC
configure:1357: result: no
configure:1328: checking for RCC
configure:1357: result: no
configure:1328: checking for xlC_r
configure:1357: result: no
configure:1328: checking for xlC
configure:1357: result: no
configure:1370: checking for C++ compiler version
configure:1373: g++ --version </dev/null >&5
./configure: line 1374: g++: command not found
configure:1376: $? = 127
configure:1378: g++ -v </dev/null >&5
./configure: line 1379: g++: command not found
configure:1381: $? = 127
configure:1383: g++ -V </dev/null >&5
./configure: line 1384: g++: command not found
configure:1386: $? = 127
configure:1409: checking for C++ compiler default output file name
configure:1412: g++    conftest.cc  >&5
./configure: line 1413: g++: command not found
configure:1415: $? = 127
configure: failed program was:
| /* confdefs.h.  */
|
| #define PACKAGE_NAME "Cherry Keyboard Tools"
| #define PACKAGE_TARNAME "cherry-keyboard-tools"
| #define PACKAGE_VERSION "1.0.0-1"
| #define PACKAGE_STRING "Cherry Keyboard Tools 1.0.0-1"
| #define PACKAGE_BUGREPORT "cymotion@cherry.de"
| /* end confdefs.h.  */
|
| int
| main ()
| {
|
|   ;
|   return 0;
| }
configure:1454: error: C++ compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=

## ----------------- ##
## Output variables. ##
## ----------------- ##

CPPFLAGS=''
CXX='g++'
CXXFLAGS=''
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EXEEXT=''
LDFLAGS=''
LIBOBJS=''
LIBS=''
LIBTOOL=''
LTLIBOBJS=''
MSGFMT=''
OBJEXT=''
PACKAGE_BUGREPORT='cymotion@cherry.de'
PACKAGE_NAME='Cherry Keyboard Tools'
PACKAGE_STRING='Cherry Keyboard Tools 1.0.0-1'
PACKAGE_TARNAME='cherry-keyboard-tools'
PACKAGE_VERSION='1.0.0-1'
PATH_SEPARATOR=':'
SHELL='/bin/sh'
ac_ct_CXX='g++'
ac_km_components=''
bindir='${exec_prefix}/bin'
build_alias=''
componentsubdirs=''
datadir='${prefix}/share'
exec_prefix='NONE'
host_alias=''
includedir='${prefix}/include'
infodir='${prefix}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
prefix='NONE'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_BUGREPORT "cymotion@cherry.de"
#define PACKAGE_NAME "Cherry Keyboard Tools"
#define PACKAGE_STRING "Cherry Keyboard Tools 1.0.0-1"
#define PACKAGE_TARNAME "cherry-keyboard-tools"
#define PACKAGE_VERSION "1.0.0-1"

configure: exit 77

---

### Post by vigleik on 2006-06-21
[QUOTE=KimJarvis]
./configure: line 1413: g++: command not found
[/QUOTE]

Did you install build-essential? You don't seem to have a c++ compiler installed on your system. (Yes, I think it's silly not to have build-essential installed by default.)

Anyway, even though there are several howto's on this forum and elsewhere, recompiling your kernel is a rather hard thing to do if you're new to linux, and while installing build-essential is the first step you'll probably have more problems to solve before you're done. But you might as well install build-essential and try again.

Vigleik

---

### Post by KimJarvis on 2006-06-22
Thanks for your advice Vigleik, I installed build-essential, tried configure again, libtool was required, installed this, then config complained about missing x files.  At this point I gave up.  However.... there may be a better way

I installed keytouch.  This is a source forge project.  [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

This project has many pre made builds including a .deb file for the AMD64, pre-defined configuration files for many keyboards including the CyMotion Master Linux keyboard.  There is also documentation and an editor for building keyboard configuration files.

---

### Post by thx_1138 on 2006-12-16
Hey there
I live in Canada and I could'nt see the option of ordering  the keyboard other than in Europe or Britain on the Cherry official website. I would be quite interested in acquiring one (possibly two) and I dont know or have not found to date a site I would feel comfortable ordering off of to get one of these. I thought I would just throw out a shout for help or the directions to a site which will sell and ship to my locale? Glad to see some others working on getting these keyboards fully functional under Ubuntu!

---

### Post by kc2iel on 2007-04-07
Digikey has the keyboard in the US.  They are expensive, but hey, I don't want the windows symbol on my keyboard either.

[http://www.digikey.com/scripts/dksearch/dksus.dll?Detail?Ref=3703&Row=596574&Site=US](http://www.digikey.com/scripts/dksearch/dksus.dll?Detail?Ref=3703&Row=596574&Site=US)

I hope I got that right.

Also, in Edgy I find Keytouch in the repos.  I'll post to this thread my results, one way or another.  I hope I get this done by the end of the year...

---

### Post by reiki on 2007-06-01
DigiKey doesn't stock these (as of June 1 2007) 
I contacted Cherry to find out where to get one and as it turns out there is only ONE distributor buying these (and you can not purchase direct from this distributor). I believe DigiKey was charging $66 for them. I found a place in the US to order them for $47.51 (USD). Ground shipping is being charged out at just under $10.

The main distributor that the resellers are getting them from is expecting a shipment July 24th. These things are in pretty short supply. I wonder if I should try and order a couple :)

---

### Post by Frank Benign on 2007-06-08
reiki,

Consider getting the Cymotion Master Solar set.  It's pretty much the same as the Linux one, except it's wireless (integrated solar charger! + long-life AA rechargables) and has the win key.  The mouse is crap though - heavy, discharges quickly, but has an integrated charger, so you just plug in a charging cable and keep using it while it's reharging..

I got it from this place [http://www.keystrokesolutions.com.au/view_products.asp?ccode=KB](http://www.keystrokesolutions.com.au/view_products.asp?ccode=KB), where it's 2-3 cheaper than anywhere else.  Don't know how much they charge for international shipping, though.

---

### Post by reiki on 2007-06-10
Frank,

Thanks.... but the whole point for me even considering the Cherry Master Linux keyboard was BECAUSE it had no windows keys ... heheheh.  The Cherry keyboards are not cheap, but the ones I've used (all on point-of-sale installations) seemed pretty well made. 

However.... I can get a Saitek Eclipse for much less and the only offensive key it has is the Windows key. I am looking into making a thin veneer of a penguin that I can adhere to the Windows key cap. I am currently not considering ANY keyboard that has a bunch of keys with Windows-specific keycaps. I don't want to see shortcuts to Word or Excel. I *may* consider keyboards that have keys printed for "My Documents" only because I can work with that and it's kind of generic. If it has a SPECIFIC reference to Microsoft software, then I won't buy it... as long as I can rid myself of that Windows key.  :)

It MIGHT be easier just to use a little solvent and see if I can get the printed Windows symbol off of the keycap. I think that's going to depend a great deal on the key cap material and the printing method used to put the symbol on the key.

---

### Post by tpg on 2007-06-10
I have one of these Cherry keyboards. As a matter of fact, when I bought it, it was £2 cheaper than an identical model with a windows key instead of a penguin! :D (Cost £25).

I haven't actually tried installing the software, as I'm content with just the usual keys, although I did notice that some of the extra keys worked with Kubuntu out of the box (like volume, other media buttons, email, web browser etc.).

---

### Post by reiki on 2007-06-10
using Ubuntu, you may have a problem installing the software which I THINK was designed for SuSe. 

However the alternative is to simply use keytouch which I THINK is in the repos and there's a couple of files for you at [http://keytouch.sourceforge.net/keyboards_cherry.php](http://keytouch.sourceforge.net/keyboards_cherry.php) to make use of all of the Master Linux keyboard keys.

By the way. How do you LIKE that keyboard? If I order it now, I may see it in mid-August and it'll cost me about $60 USD (a bit over 30 british pounds I would think).

From your experience.... is it worth it? I ask because I can get a Saitek eclipse for about half of that.

thanks!

---

### Post by tpg on 2007-06-10
I'm no keyboard expert, but it's definitely the best keyboard I've ever used! It has a good solid feel to it, and the keys are weighted nicely (the keys also make a very satisfying solid clicking sound :)). I've had it for a few months, no problems at all, and from the looks of it it should last a good long time.

I don't know anything about the Saitek keyboard, so I don't know how good it is in relation to that, but I would say that yes, the Cherry is worth it.

---

