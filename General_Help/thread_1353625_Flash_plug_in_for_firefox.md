---
title: "Flash plug in for firefox"
date: 2009-12-13
forum: General Help
---

### Post by Jibber on 2009-12-13
Hey guys, this is my first time using Linux, any who, I am having issues with the flash plug in, every time I tried to install it, it gives me this error message:

"installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Selecting previously deselected package flashplugin-installer. 
(Reading database ...  (Reading database ... 5%dpkg: unrecoverable fatal error, aborting: 
 files list file for package 'xserver-xorg-video-v4l' is missing final newline"

Iv tried every way to download/install it, but all met with the same error, Iv also tried searching for help with google, but there doesnt seem to be any case that is exactly like mine, I am running a freshly installed Ubuntu 9.10. any help would be appreciated

---

### Post by staf0048 on 2009-12-13
Question:  Are you installing flash from the Adobe website or from the repositories?

---

### Post by Jibber on 2009-12-13
Tried both

---

### Post by staf0048 on 2009-12-13
Odd.  It must be something with 9.10.  I've not yet upgraded to that version yet, so I really couldn't tell you why it's giving you a hard time.  

Instead of firefox you could give chrome a try, it comes with flash pre-installed.  There's a beta version for Linux available now at: [http://www.google.com/chrome?platform=linux&hl=en](http://www.google.com/chrome?platform=linux&hl=en)

I'm not a huge fan of the Google empire takeover, but I must admit it's one fast browser...

---

### Post by Jibber on 2009-12-13
ok damn it, didnt work, I got a similar error, it seems like I cant install anything

"Selecting previously deselected package flashplugin-installer. 
(Reading database ...  (Reading database ... 5%dpkg: unrecoverable fatal error, aborting: 
 files list file for package 'xserver-xorg-video-v4l' is missing final newline"

---

### Post by Vishnu V on 2009-12-13
Try this
open aterminal and type
```

sudo apt-get upgrade
sudo apt-get update

```
and now install the flash plug-in

---

### Post by Jibber on 2009-12-13
when I did "sudo apt-get upgrade" the last line was the same error with "E: Sub-process /usr/bin/dpkg returned an error code (2)", needless to say, it didnt work

---

### Post by LuisGMarine on 2009-12-13
Is this on a 32-bit or 64-bit system?

---

### Post by Jibber on 2009-12-13
32-bits

---

### Post by LuisGMarine on 2009-12-13
So even if you open up the Ubuntu Software Center (**Applications > Ubuntu Software Center**) and type in flash and install it that way gives you errors?

---

### Post by Jibber on 2009-12-13
yes, it kind of loads slowly at first then it suddenly hits 50% and the error pops up

---

### Post by LuisGMarine on 2009-12-13
Ok lets start from the very beginning.  Open up terminal and type in:
```

sudo apt-get update
```

then type in:

```
sudo apt-get upgrade
```

make sure that if you get errors on either of those two commands you post the WHOLE OUTPUT don't know put a snip of the error as you might be missing certain parts that are critical to helping pin point the exact cause.  Post back as soon as you are done =)

---

### Post by Jibber on 2009-12-13
no error for sudo apt-get update

but for sudo apt-get upgrade:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-50 libdns50 libisc50 libisccc50 libisccfg50
  liblwres50 linux-generic linux-headers-generic linux-image-generic
  sreadahead
The following packages will be upgraded:
  adduser apparmor apparmor-utils apport apport-gtk avahi-autoipd avahi-daemon
  binutils brasero checkbox checkbox-gtk cups cups-bsd cups-client cups-common
  devicekit-disks empathy empathy-doc evince evolution evolution-common
  evolution-documentation-en evolution-indicator evolution-plugins f-spot
  firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-gnome-support fuse-utils gdm gnome-about gnome-desktop-data
  gnome-screensaver gnome-settings-daemon grub-common grub-pc
  gstreamer0.10-alsa gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-x gtk2-engines
  gtk2-engines-murrine gtk2-engines-pixbuf ibus ibus-gtk initscripts
  kerneloops-daemon libapparmor-perl libapparmor1 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core6 libavahi-glib1
  libavahi-gobject0 libavahi-ui0 libbrasero-media0 libclutter-gtk-0.10-0
  libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1
  libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30
  libenchant1c2a libevdocument1 libevview1 libfuse2 libgail-common libgail18
  libgd2-xpm libgnome-desktop-2-11 libgstreamer-plugins-base0.10-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgudev-1.0-0 libhtml-parser-perl libibus1
  libindicate-gtk1 libindicate3 libnautilus-extension1 libpoppler-glib4
  libpoppler5 libpython2.6 libsmbclient libudev0 libvorbis0a libvorbisenc2
  libvorbisfile3 libwbclient0 linux-firmware linux-libc-dev nautilus
  nautilus-data ntpdate nvidia-common poppler-utils python python-apport
  python-avahi python-ibus python-minimal python-problem-report
  python-ubuntuone-client python2.6 python2.6-minimal rhythmbox samba-common
  samba-common-bin smbclient system-tools-backends sysv-rc sysvinit-utils
  totem totem-common totem-mozilla totem-plugins tzdata ubuntu-xsplash-artwork
  ubuntuone-client ubuntuone-client-gnome udev update-manager
  update-manager-core x11-common xorg xsane xsane-common xserver-xorg
  xserver-xorg-input-all xserver-xorg-video-all xsplash xulrunner-1.9.1
  xulrunner-1.9.1-gnome-support
141 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
Need to get 0B/80.6MB of archives.
After this operation, 3,916kB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 5%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'xserver-xorg-video-v4l' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by LuisGMarine on 2009-12-13
Something is wrong with that package called 'xserver-xorg-video-v4l'

Sorry but it's 3 AM in the morning right now, and my brain is shutting down on me.  I'll have to look into this in the morning.  Hopefully someone else might give you a command to reconfigure that package and try to fix it.  Or you can google to see what you can come up with.

---

