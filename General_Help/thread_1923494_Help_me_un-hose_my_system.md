---
title: "Help me un-hose my system"
date: 2012-02-10
forum: General Help
---

### Post by Yadda on 2012-02-10
So, I did a spectacularly stupid thing in a misguided attempt to get something to work and uninstalled pygobject. Well it pulled a huge part of the os out with it. 

I've been reinstalling programs and libraries as I find them missing but my biggest issue is that the Unity menu (the thing with the Ubuntu symbol on it) is still totally hosed. All the programs are missing from it and clicking on "Media Apps" "Internet Apps" etc. causes my window manager to crash alltogether, sometimes requireing a reboot.

I'd like to get it back to the point where applications are showing up when I search for them and where clicking an icon doesn't make the system crash.

So, any ideas of how I can put the pieces back together without reinstalling?

Thanks!

---

### Post by 23dornot23d on 2012-02-10
You could try

[B]sudo apt-get update

sudo apt-get install aptitude

sudo aptitude update

sudo aptitude install [/B]pygobject 
 (are you sure it was this - all I find is python-gobject-2-dev python-gi-dev ) ok found it 
[B][COLOR=Red][http://live.gnome.org/PyGObject](http://live.gnome.org/PyGObject)[/COLOR]

sudo aptitude reinstall unity


[/B]
Best I can think of at the moment ....[B] it may say there are lots of dependency problems - if so - post the results it shows ..... someone may pick up
more from it .....


Takes 30 mins to re-install though .... ( depends how borked it has become )
[/B]

---

### Post by nikonian on 2012-02-10
They should make a command (I'm serious) that is:

```

sudo apt-unhose

```

Which reverses **everything** that was executed in the previous command

---

### Post by Yadda on 2012-02-10
Followed 23dornot23d's instructions with no luck. The same problems persist.

---

### Post by 23dornot23d on 2012-02-10
Can you post some output from this ....
[B]
sudo aptitude safe-upgrade[/B]

do [COLOR=Red]**not**[/COLOR] answer y to it ...... answer n

copy and post the results ..... so I can see what it says please.

mine comes back with this as an example of what you should see

> 
root@keith-Aspire-7730ZG:/home/keith/Documents# aptitude safe-upgrade
Resolving dependencies...                
The following NEW packages will be installed:
  libgstreamer-plugins-bad0.10-0{a} libspandsp2{a} libvo-aacenc0{a} 
  libvo-amrwbenc0{a} libvpx1{a} libzvbi-common{a} libzvbi0{a} 
  linux-image-3.2.0-15-generic{a} 
The following packages will be REMOVED:
  libvpx0{u} 
The following packages will be upgraded:
  apparmor appmenu-gtk appmenu-gtk3 bluez bluez-alsa bluez-cups 
  command-not-found command-not-found-data cups cups-bsd cups-client 
  cups-common cups-ppdc file-roller friendly-recovery ghostscript 
  ghostscript-cups ghostscript-x gnome-control-center 
  gnome-control-center-data gnome-menus gstreamer0.10-gconf 
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-good 
  gstreamer0.10-pulseaudio gzip hpijs hplip hplip-data 
  indicator-application indicator-appmenu indicator-session indicator-sound 
  language-selector-common language-selector-kde libavcodec53 libavdevice53 
  libavformat53 libavutil51 libbluetooth3 libc-bin libc-dev-bin libc6 
  libc6-dev libcups2 libcups2-dev libcupscgi1 libcupsdriver1 libcupsimage2 
  libcupsmime1 libcupsppdc1 libegl1-mesa libegl1-mesa-dev 
  libegl1-mesa-drivers libgbm-dev libgbm1 libgl1-mesa-dev libgl1-mesa-dri 
  libgl1-mesa-dri-dbg libgl1-mesa-glx libglapi-mesa libgles2-mesa 
  libgles2-mesa-dev libglu1-mesa libglu1-mesa-dev libgnome-control-center1 
  libgnome-menu-3-0 libgs9 libgs9-common libhpmud0 libido3-0.1-0 
  libmission-control-plugins0 libmlt++3 libmlt-data libmlt4 
  libnautilus-extension1a libnewt0.52 libnih-dbus1 libnih1 libopenvg1-mesa 
  libpam-modules libpam-modules-bin libpam-runtime libpam0g libpam0g-dev 
  libpixman-1-0 libpixman-1-dev libpostproc52 libpulse-mainloop-glib0 
  libpulse0 libpulsedsp libsane-hpaio libswscale2 libtelepathy-glib0 
  libxatracker1 libxcb-dri2-0 libxcb-dri2-0-dev libxcb-glx0 libxcb-glx0-dev 
  libxcb-randr0 libxcb-render0 libxcb-render0-dev libxcb-shape0 
  libxcb-shape0-dev libxcb-shm0 libxcb-shm0-dev libxcb-sync0 
  libxcb-sync0-dev libxcb-util0 libxcb-xfixes0 libxcb-xfixes0-dev 
  libxcb-xv0 libxcb1 libxcb1-dev linux-generic linux-image-generic 
  linux-libc-dev melt mesa-common-dev modemmanager multiarch-support 
  nautilus nautilus-data printer-driver-hpcups printer-driver-hpijs 
  pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth 
  pulseaudio-module-x11 pulseaudio-utils python-gi python-gobject 
  python-mlt3 synaptic telepathy-mission-control-5 upstart usb-modeswitch 
  whiptail 
The following packages are RECOMMENDED but will NOT be installed:
  manpages-dev 
138 packages upgraded, 8 newly installed, 1 to remove and 0 not upgraded.
Need to get 115 MB of archives. After unpacking 116 MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
root@keith-Aspire-7730ZG:/home/keith/Documents# 


---

### Post by Yadda on 2012-02-10
The output is:

```

No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         

```

---

### Post by Paqman on 2012-02-10
Reinstall [ubuntu-desktop]("apt:ubuntu-desktop"). That should drag in everything you need for a working desktop.

---

### Post by Yadda on 2012-02-10
reinstalling ubuntu-desktop resulted in an additional 50MB of packages from where I was. I'm reasonably confident I've reinstalled most of what went missing with that.

That said, the Unity menu is still exhibiting the same problems.

---

### Post by Paqman on 2012-02-10
> **Yadda said:**
> 
That said, the Unity menu is still exhibiting the same problems.

Try:
```
unity --reset-icons
```
and if it's still not working, go for:
```
unity --reset
```
That should zero unity back to it's default settings.

---

### Post by Yadda on 2012-02-13
Ok so I reset unity and compiz. I also reinstalled compiz, unity, ubuntu-desktop and bamf*. If I'm running unity from the terminal I get the following output:

```
WARN  2012-02-13 09:12:41 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window79691782: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
```

When I click the "Media Apps" icon in the Unity menu, I get a segfault.

---

