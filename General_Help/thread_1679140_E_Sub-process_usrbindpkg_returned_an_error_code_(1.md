---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-01-31
forum: General Help
---

### Post by clooless001 on 2011-01-31
I was recently trying to install fglrx through synaptic, halfway through i got an error message (Can't remember what it said)

Now when i open synaptic i get a message saying:

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

If i go Edit > Fix broken packages and try to apply i get:

E: /var/cache/apt/archives/libc-bin_2.11.1-0ubuntu7.7_i386.deb: unable to create updated files list file for package libc-bin

Since this has happened i've realised when i run java (Specifcally runescape) it will randomly quit java, this can be after 5 minutes or an hour, and on occasion it has hung my current session and taken me back into the login screen, causing me to lose any documents i was working on.

I'm quite an ubuntu noob but i know the basics,
All help appreciated!

---

### Post by clooless001 on 2011-02-01
Bump,
I really need help .. anything at all you can do to help me will be appreciated.
I'm going now and won't be home for 6 hours,
Thanks.

---

### Post by ashickur.noor on 2011-02-01
run ```
sudo apt-get install -f
```

---

### Post by clooless001 on 2011-02-01
```
dpkg: warning: files list file for package `libsoup-gnome2.4-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fontconfig' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-settings-daemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcurl3-gnutls' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lsb-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsoup2.4-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtasn1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gconf-editor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tk8.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgd2-xpm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsolidcontrol4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-papyon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtop2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libuuid1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-system-monitor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `screensaver-default-images' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lzma' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxinerama1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl1.2debian' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evolution-data-server-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-wnck' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plymouth-x11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpisync1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdepimlibs-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgegl-0.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `eog' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-sis' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cvs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-dbus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xulrunner-1.9' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xcursor-themes' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lightsoff' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwps-0.1-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplasma-applet-system-monitor4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjs-jquery' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbind9-60' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcrypt11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libupnp3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavcodec52' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-v4l' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexif12' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdbm3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libesd-alsa0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcairo2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libibus1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-public-key' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgstfarsight0.10-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `myspell-en-au' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `man-db' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libffi5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libenca0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgraphite3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgamin0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `module-init-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libflac8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gettext-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvorbisfile3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `glines' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libperl5.10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomecanvas2-dbg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-user-guide' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbus-1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-applets-dbg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgmp3c2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cups-ppdc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango1.0-0-dbg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxplc0.3.13' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xscreensaver-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `desktop-file-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `example-content' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gpgv' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `login' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgoocanvas3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-amd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telnet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11-xkb-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-plugins-base-apps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireless-crda' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `laptop-detect' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `makedev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `initramfs-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libprotobuf5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-twisted-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcelt0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gtkspell' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-terminal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-emailmerge' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxmuu1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libisccfg60' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-parser-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-shm0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `finger' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio-module-x11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubufox' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfonts-mathml' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsysfs2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bcmwl-modaliases' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debianutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfreetype6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sudo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsane' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cupsddk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopts25' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `coreutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavutil49' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ure' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-system-data2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `empathy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `esound-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gvfs-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgl1-mesa-dri' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdmcp6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmpfr1ldbl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-speech7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `shared-mime-info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome2-dbg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libraw1394-11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk1.2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mktemp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit-gobject-1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-sip' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libart-2.0-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmagickcore2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mono-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnome2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gimp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dash' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libltdl-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `memtest86+' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libelf1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gtk2-engines-murrine' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomekbd4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librecode0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxft2-dbg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpth20' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mono-2.0-gac' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pitivi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjson-glib-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgssdp-1.0-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apturl-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `java-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gir1.0-clutter-gtk-0.10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `empathy-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpod-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sane-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libclutter-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtext-wrapi18n-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfftw3-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbonoboui2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-client-core-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tcpd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pkg-resources' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkspell0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexempi3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-libxml-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-input-vmmouse' missing, assuming package has no files currently installed.
(Reading database ... 25 files and directories currently installed.)
Preparing to replace libc-bin 2.11.1-0ubuntu7.5 (using .../libc-bin_2.11.1-0ubuntu7.7_i386.deb) ...
Unpacking replacement libc-bin ...
dpkg: error processing /var/cache/apt/archives/libc-bin_2.11.1-0ubuntu7.7_i386.deb (--unpack):
 unable to create updated files list file for package libc-bin: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libc-bin_2.11.1-0ubuntu7.7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ben@ben-desktop:~$ 
```


There was more at the top but it cut it off..

Please use #Code tags.

---

### Post by clooless001 on 2011-02-01
I think there is some problem with my package list .. Mainly that there isn't one :S
Any way i can .. get another?

---

### Post by directhex on 2011-02-01
Sounds like some severe filesystem corruption, for all those files to be empty.

Reinstalling the named packages should restore the files lists.

---

### Post by piquat on 2011-02-01
.

---

### Post by clooless001 on 2011-02-01
> **directhex said:**
> Sounds like some severe filesystem corruption, for all those files to be empty.

Reinstalling the named packages should restore the files lists.

How would i do that? I tried to do it through terminal with
 ```
sudo apt-get install libsoup-gnome2.4-1
```But that returned 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsoup-gnome2.4-1 is already the newest version.
libsoup-gnome2.4-1 set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.5) but 2.11.1-0ubuntu7.7 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by Krytarik on 2011-02-01
> **clooless001 said:**
> How would i do that? I tried to do it through terminal with
 ```
sudo apt-get install libsoup-gnome2.4-1
```But that returned 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsoup-gnome2.4-1 is already the newest version.
[COLOR=Red] libsoup-gnome2.4-1 set to manually installed.[/COLOR]
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.5) but 2.11.1-0ubuntu7.7 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
That makes me suspicious, check in "System -> Administration -> Software Sources -> Ubuntu Software" if at least the first 4 options are checked, and if "Download from" is set correctly.

---

### Post by clooless001 on 2011-02-01
> **Krytarik said:**
> That makes me suspicious, check in "System -> Administration -> Software Sources -> Ubuntu Software" if at least the first 4 options are checked, and if "Download from" is set correctly.

Yes, the first four boxes are ticked and the download from option is set to uk, no problems there :S

---

### Post by Krytarik on 2011-02-01
Please run each of the following commands and post its output here, in code tags please (like you just yet learned;)).
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
```

---

### Post by clooless001 on 2011-02-01
> **Krytarik said:**
> Please run each of the following commands and post its output here, in code tags please (like you just yet learned;)).
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
```

sudo apt-get update
```
Hit http://gb.archive.ubuntu.com lucid Release.gpg
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB    
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB          
Get: 1 http://security.ubuntu.com lucid-security Release.gpg [198B]            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB   
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ hardy/partner Translation-en_GB       
Hit http://archive.ubuntu.com lucid Release.gpg                                
Hit http://archive.ubuntu.com jaunty Release.gpg                               
Hit http://archive.ubuntu.com/ubuntu/ jaunty/universe Translation-en_GB        
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB      
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB    
Hit http://gb.archive.ubuntu.com hardy-backports Release.gpg                   
Ign http://gb.archive.ubuntu.com/ubuntu/ hardy-backports/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ hardy-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ hardy-backports/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ hardy-backports/multiverse Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Get: 2 http://security.ubuntu.com lucid-security Release [44.7kB]              
Hit http://gb.archive.ubuntu.com lucid Release                                 
Hit http://archive.ubuntu.com lucid Release                                    
Hit http://archive.canonical.com hardy Release                                 
Hit http://gb.archive.ubuntu.com hardy-backports Release                       
Hit http://archive.ubuntu.com jaunty Release                                   
Hit http://gb.archive.ubuntu.com lucid/restricted Packages                     
Hit http://archive.ubuntu.com lucid/main Sources                               
Hit http://archive.canonical.com hardy/partner Packages              
Hit http://gb.archive.ubuntu.com lucid/main Packages                           
Hit http://gb.archive.ubuntu.com lucid/universe Packages                       
Hit http://gb.archive.ubuntu.com lucid/restricted Sources                      
Hit http://gb.archive.ubuntu.com lucid/main Sources                            
Hit http://archive.ubuntu.com lucid/restricted Sources                         
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://gb.archive.ubuntu.com lucid/multiverse Sources            
Hit http://gb.archive.ubuntu.com lucid/universe Sources
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-backports/main Packages         
Hit http://gb.archive.ubuntu.com hardy-backports/restricted Packages   
Hit http://gb.archive.ubuntu.com hardy-backports/universe Packages     
Hit http://gb.archive.ubuntu.com hardy-backports/multiverse Packages   
Hit http://gb.archive.ubuntu.com hardy-backports/main Sources          
Hit http://gb.archive.ubuntu.com hardy-backports/restricted Sources    
Hit http://gb.archive.ubuntu.com hardy-backports/universe Sources      
Hit http://archive.ubuntu.com jaunty/universe Packages                 
Hit http://gb.archive.ubuntu.com hardy-backports/multiverse Sources    
Get: 3 http://security.ubuntu.com lucid-security/restricted Packages [14B]
Get: 4 http://security.ubuntu.com lucid-security/main Packages [131kB]
Get: 5 http://security.ubuntu.com lucid-security/universe Packages [61.0kB]
Get: 6 http://security.ubuntu.com lucid-security/restricted Sources [14B]
Get: 7 http://security.ubuntu.com lucid-security/main Sources [43.3kB]
Get: 8 http://security.ubuntu.com lucid-security/multiverse Sources [660B]
Get: 9 http://security.ubuntu.com lucid-security/universe Sources [17.6kB]
Get: 10 http://security.ubuntu.com lucid-security/multiverse Packages [2,003B]
Fetched 300kB in 3s (87.5kB/s)                             
Reading package lists... Done

```

sudo apt-get upgrade
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
E: Unmet dependencies. Try using -f.

```


sudo apt-get --fix-broken install
```
dpkg: warning: files list file for package `libsoup-gnome2.4-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fontconfig' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-settings-daemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcurl3-gnutls' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lsb-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsoup2.4-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtasn1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gconf-editor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tk8.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgd2-xpm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsolidcontrol4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-papyon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtop2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libuuid1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-system-monitor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `screensaver-default-images' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lzma' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxinerama1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl1.2debian' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evolution-data-server-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-wnck' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plymouth-x11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpisync1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdepimlibs-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgegl-0.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `eog' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-sis' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cvs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-dbus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xulrunner-1.9' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xcursor-themes' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lightsoff' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwps-0.1-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplasma-applet-system-monitor4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjs-jquery' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbind9-60' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcrypt11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libupnp3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavcodec52' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-v4l' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexif12' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdbm3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libesd-alsa0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcairo2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libibus1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-public-key' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgstfarsight0.10-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `myspell-en-au' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `man-db' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libffi5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libenca0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgraphite3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgamin0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `module-init-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libflac8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gettext-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvorbisfile3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `glines' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libperl5.10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomecanvas2-dbg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-user-guide' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbus-1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-applets-dbg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgmp3c2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cups-ppdc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango1.0-0-dbg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxplc0.3.13' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xscreensaver-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `desktop-file-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `example-content' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gpgv' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `login' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgoocanvas3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-amd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telnet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11-xkb-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-plugins-base-apps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireless-crda' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `laptop-detect' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `makedev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `initramfs-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libprotobuf5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-twisted-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcelt0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gtkspell' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-terminal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-emailmerge' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxmuu1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libisccfg60' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-parser-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-shm0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `finger' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio-module-x11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubufox' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfonts-mathml' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsysfs2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bcmwl-modaliases' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debianutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfreetype6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sudo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsane' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cupsddk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopts25' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `coreutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavutil49' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ure' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-system-data2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `empathy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `esound-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gvfs-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgl1-mesa-dri' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdmcp6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmpfr1ldbl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-speech7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `shared-mime-info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome2-dbg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libraw1394-11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk1.2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mktemp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit-gobject-1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-sip' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libart-2.0-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmagickcore2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mono-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnome2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gimp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dash' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libltdl-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `memtest86+' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libelf1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gtk2-engines-murrine' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomekbd4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librecode0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxft2-dbg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpth20' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mono-2.0-gac' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pitivi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjson-glib-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgssdp-1.0-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apturl-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `java-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gir1.0-clutter-gtk-0.10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `empathy-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpod-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sane-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libclutter-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtext-wrapi18n-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfftw3-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbonoboui2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-client-core-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tcpd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pkg-resources' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkspell0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexempi3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-libxml-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-input-vmmouse' missing, assuming package has no files currently installed.
(Reading database ... 25 files and directories currently installed.)
Preparing to replace libc-bin 2.11.1-0ubuntu7.5 (using .../libc-bin_2.11.1-0ubuntu7.7_i386.deb) ...
Unpacking replacement libc-bin ...
dpkg: error processing /var/cache/apt/archives/libc-bin_2.11.1-0ubuntu7.7_i386.deb (--unpack):
 unable to create updated files list file for package libc-bin: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libc-bin_2.11.1-0ubuntu7.7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
There was more to that one, but again, it got cut off.

sudo apt-get --fix-missing install
```
ben@ben-desktop:~$ sudo apt-get --fix-missing install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
E: Unmet dependencies. Try using -f.

```

And yeah, I'm proud of my new ability to make code boxes ;D

---

### Post by Krytarik on 2011-02-01
Please try to follow the steps given in this guide:
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

### Post by clooless001 on 2011-02-01
> **Krytarik said:**
> Please try to follow the steps given in this guide:
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

I have done, thanks.
Now just to keep my fingers crossed and play the waiting game.

---

