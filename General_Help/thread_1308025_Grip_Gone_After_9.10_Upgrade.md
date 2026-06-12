---
title: "Grip Gone After 9.10 Upgrade"
date: 2009-10-31
forum: General Help
---

### Post by dlobo on 2009-10-31
All,

I just noticed that grip is gone from my Ubuntu 9.10 after the installation.
I went to Synaptic to re-install it, but I got this message:
<message>
grip:

Package grip has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
</message>

Does this mean that grip won't be available anymore in Ubuntu? If that's the case, can anyone recommend a good alternative for it?

Thanks a lot
Respectfully

dmlobo

---

### Post by p999t on 2009-10-31
Try ripperx or abcde both are in the repositories

Peter

---

### Post by Subban on 2009-10-31
I was dissapointed to see Grip gone myself as well, I have been using RipperX for the last couple days but it is not as good sadly. My biggest gripe with it is that the CDDB entries for many of my mix CD's I am encoding use / to separate artist/song, and I am forced to edit every entry by hand prior to ripping :/

---

### Post by WileyGaia on 2009-12-18
I am still on 8.10 and using GRIP. The thing is my IPOD does not recognize any songs where the artist and song name from cddb are separated with a forward slash /

Is this normal? I think I saw something in GRIP which can filter out or replace these characters...

If I were to upgrade to 9.10, which ripper can offer the same functionality? i.e. filter out or replace characters when tagging the track from cddb?

---

### Post by StuartN on 2009-12-18
> **WileyGaia said:**
> Is this normal?

If I were to upgrade to 9.10, which ripper can offer the same functionality? i.e. filter out or replace characters when tagging the track from cddb?

I had not noticed any problems with the contents of tags made by Grip, other than a Unicode character set problem, but there is a "Replace incompatible characters with hex" setting under Misc configuration settings.

EasyTag seems to offer many ways to correct tags (and filenames), so if neither of Ripperx or Abcde generate compatible tags, then you can process them before connecting the iPod.

---

### Post by pbrane on 2009-12-18
You can always download the source from [http://nostatic.org/grip/grip-download.shtml]("http://nostatic.org/grip/grip-download.shtml") and build it.
That's what I did.

---

### Post by linuxguru1 on 2010-06-17
> **pbrane said:**
> You can always download the source from [http://nostatic.org/grip/grip-download.shtml]("http://nostatic.org/grip/grip-download.shtml") and build it.
That's what I did.

*bump*

I'm trying to do so, but I think I'm missing a couple of libraries. Can anyone help me out?

```
$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/stefaan/Desktop/grip-3.2.0/missing: Unknown `--run' option
Try `/home/stefaan/Desktop/grip-3.2.0/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking linux/cdrom.h usability... yes
checking linux/cdrom.h presence... yes
checking for linux/cdrom.h... yes
checking linux/ucdrom.h usability... no
checking linux/ucdrom.h presence... no
checking for linux/ucdrom.h... no
checking sys/cdio.h usability... no
checking sys/cdio.h presence... no
checking for sys/cdio.h... no
checking io/cam/cdrom.h usability... no
checking io/cam/cdrom.h presence... no
checking for io/cam/cdrom.h... no
checking sys/mntent.h usability... no
checking sys/mntent.h presence... no
checking for sys/mntent.h... no
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking sys/audio.io.h usability... no
checking sys/audio.io.h presence... no
checking for sys/audio.io.h... no
checking sun/audioio.h usability... no
checking sun/audioio.h presence... no
checking for sun/audioio.h... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 >= 2.2.0... yes
checking GNOME_CFLAGS... -DORBIT2=1 -pthread -D_REENTRANT -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/directfb -I/usr/include/libpng12  
checking GNOME_LIBS... -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgconf-2 -lgmodule-2.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for vte... Package vte was not found in the pkg-config search path. Perhaps you should add the directory containing `vte.pc' to the PKG_CONFIG_PATH environment variable No package 'vte' found
configure: error: Library requirements (vte) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
$

```

Thanks.

---

### Post by StuartN on 2010-06-17
> **linuxguru1 said:**
> I'm trying to do so, but I think I'm missing a couple of libraries. Can anyone help me out?

Possibly libvte9 or libvte-common and libvte-dev

But would the Ubuntu Grip package at [http://packages.ubuntu.com/jaunty/grip](http://packages.ubuntu.com/jaunty/grip) not work?

---

### Post by linuxguru1 on 2010-06-17
> **StuartN said:**
> Possibly libvte9 or libvte-common and libvte-dev

But would the Ubuntu Grip package at [http://packages.ubuntu.com/jaunty/grip](http://packages.ubuntu.com/jaunty/grip) not work?

After installing those libraries with the sudo apt-get command, and getting a library called "libcurl", I was able to compile Grip.

Thanks =]

edit:
I still seem to be having a problem... grip's working fine, except that whenever I try to rip + encode, it gives me an error.
"Invalid encoder executable, check the encode config."
I checked the config. It's configured to use lame to encode wavs to mp3s. I have lame installed. When I run lame from the commandline with all the same options (-h -b 128 ), it works fine.

[Link to a screenshot of my encoder-config](http://www.imgdumper.nl/uploads3/4c1a1399d59c0/4c1a1399cdcbb-Screenshot.png)

---

### Post by oldos2er on 2010-06-17
Did you install libmp3lame-dev too?

---

### Post by linuxguru1 on 2010-06-19
It wasn't installed, but I installed it. Still no luck with grip though... the same errormessage persists.

---

### Post by dcstar on 2010-06-19
Grip PPA for Lucid:

[http://ubuntuforums.org/showpost.php?p=9203816&postcount=32](http://ubuntuforums.org/showpost.php?p=9203816&postcount=32)

Encoder executable path with lame installed (and selected):
```

/usr/bin/lame
```

---

### Post by nullman on 2010-11-06
> **linuxguru1 said:**
> It wasn't installed, but I installed it. Still no luck with grip though... the same errormessage persists.
Try rebuilding grip.  The dev package probably installs libraries that need to be available at build time.

---

### Post by nullman on 2010-11-06
Here were the steps I took to build and install grip in Ubuntu 10.10:

```
dir=${HOME}/tmp/grip
sudo apt-get install libgnomeui-dev libmp3lame-dev libvte-dev libcdparanoia-dev libid3-3.8.3-dev libcurl4-openssl-dev
mkdir -p ${dir}
pushd ${dir}
wget http://downloads.sourceforge.net/project/grip/grip/3.2.0/grip-3.2.0.tar.gz
tar zxvf grip*.tar.gz
cd grip-3.2.0
./configure && make && sudo make install
rm -rf ${dir}
popd
```

---

