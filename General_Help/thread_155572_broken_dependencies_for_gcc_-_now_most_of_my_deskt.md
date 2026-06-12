---
title: "broken dependencies for gcc - now most of my desktop is broken"
date: 2006-04-05
forum: General Help
---

### Post by Roobert on 2006-04-05
Ugh, ok long story: (Note: I'm on windows typing this, so I'm working from memory here).

I was trying to install teTex3 rpms, and to do so, I had to install additional dependencies such as libgcc, gcc4.0,3-1ubuntu3, etc,etc,. It became apparant that too many older dependencies were being broken to allow teTex3 to be installed, so I think I tried to remove the newer gcc and revert back to the older one using Synaptic, but in so doing, removed most of the gnome-desktop (180 packages). Because of this, nautilus and terminal were removed so I can't access any of my files anymore, and since there's no command line, I can't leave the desktop. 

Synaptic still works, so I tried to remove the newer gcc so I could re-install an older version (and presumably my gnome-desktop) but I'm caught in a dependency loop in that the older version can't be installed because the newer one is set to be installed. But if I try to uninstall the newer version, I get warned that ESSENTIAL files could be removed and my system rendered unusable! 

Is there some way of re-installing gcc and all its' dependent packages without doing a complete OS re-install? I would just put the Breezy install CD in and reformat, but I have a lot of data on my home directory that I can't delete!

Thanks

~ Eric.

---

### Post by psychicdragon on 2006-04-05
You could try to install the ubuntu-desktop package, which will install all the default packages and remove any that conflict with them (hopefully).

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Roobert on 2006-04-05
Ok, here's what sudo apt-get install build-essential gives me:

```
Reading package lists...
Building dependency tree...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
```

And trying sudo apt-get install ubuntu-desktop is similar:

```
Reading package lists...
Building dependency tree...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: bluez-pin but it is not going to be installed
                  Depends: bug-buddy but it is not going to be installed
                  Depends: contact-lookup-applet but it is not going to be installed
                  Depends: eog but it is not going to be installed
                  Depends: evince but it is not going to be installed
                  Depends: evolution but it is not going to be installed
                  Depends: evolution-exchange but it is not going to be installed
                  Depends: evolution-plugins but it is not going to be installed
                  Depends: evolution-webcal but it is not going to be installed
                  Depends: file-roller but it is not going to be installed
                  Depends: firefox but it is not going to be installed
                  Depends: firefox-gnome-support but it is not going to be installed
                  Depends: gcalctool but it is not going to be installed
                  Depends: gconf-editor but it is not going to be installed
                  Depends: gdm but it is not going to be installed
                  Depends: gedit but it is not going to be installed
                  Depends: gnome-about but it is not going to be installed
                  Depends: gnome-app-install but it is not going to be installed
                  Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-btdownload but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-cups-manager but it is not going to be installed
                  Depends: gnome-games but it is not going to be installed
                  Depends: gnome-media but it is not going to be installed
                  Depends: gnome-netstatus-applet but it is not going to be installed
                  Depends: gnome-nettool but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: gnome-pilot-conduits but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: gnome-spell but it is not going to be installed
                  Depends: gnome-system-monitor but it is not going to be installed
                  Depends: gnome-system-tools but it is not going to be installed
                  Depends: gnome-terminal but it is not going to be installed
                  Depends: gnome-utils but it is not going to be installed
                  Depends: gnome-volume-manager but it is not going to be installed
                  Depends: gnomemeeting but it is not going to be installed
                  Depends: gstreamer0.8-gnomevfs but it is not going to be installed
                  Depends: gstreamer0.8-misc but it is not going to be installed
                  Depends: gstreamer0.8-vorbis but it is not going to be installed
                  Depends: gthumb but it is not going to be installed
                  Depends: gucharmap but it is not going to be installed
                  Depends: hal-device-manager but it is not going to be installed
                  Depends: hwdb-client but it is not going to be installed
                  Depends: libgnome2-perl but it is not going to be installed
                  Depends: libgstreamer-gconf0.8-0 but it is not going to be installed
                  Depends: metacity but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: nautilus-cd-burner but it is not going to be installed
                  Depends: nautilus-sendto but it is not going to be installed
                  Depends: openoffice.org2 but it is not going to be installed
                  Depends: openoffice.org2-gnome but it is not going to be installed
                  Depends: python-gnome2 but it is not going to be installed
                  Depends: python-pyorbit but it is not going to be installed
                  Depends: rhythmbox but it is not going to be installed
                  Depends: serpentine but it is not going to be installed
                  Depends: sound-juicer but it is not going to be installed
                  Depends: totem but it is not going to be installed
                  Depends: tsclient but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Depends: vino but it is not going to be installed
                  Depends: yelp but it is not going to be installed
```

I need some way of forcing the base packages to re-install without erasing my partition with a complete reinstall, I think.

Any other ideas?

---

### Post by Al3xanR0 on 2006-04-05
Assuming you are still able to use Synaptic, when you perform a "Reload" are there any broken packages? (usually displayed at the bottom) I ask that because I installed a  series of Debian packages one of which broke. Once it broke Synaptic naturally displayed "1 broken" interestingly enough its idea of repairing was to remove 287 dependant packages or ESSENTIAL packages dependant on which package I tried to remove in my initial repair attempt. The long and short of it was that I managed to locate the offending package (in Synaptic) it showed with a red box next to it. reverted it back to the one Ubuntu preferred by selecting it, clicking package, then the force version option and that solved my issue. This may or may not work but it is worth giving it a shot

---

### Post by Roobert on 2006-04-05
[QUOTE=Al3xanR0]Assuming you are still able to use Synaptic, when you perform a "Reload" are there any broken packages? (usually displayed at the bottom) [/QUOTE]

No, I'm unable to use Synaptic...all I get is a text login now - Metacity appears to have been a casualty as well. Ubuntu complains that the X-Windows server doesn't appear to be running. 

[QUOTE=Al3xanR0] <snip> The long and short of it was that I managed to locate the offending package (in Synaptic) it showed with a red box next to it. reverted it back to the one Ubuntu preferred by selecting it, clicking package, then the force version option and that solved my issue. This may or may not work but it is worth giving it a shot[/QUOTE]

Thanks, but is there a way to do this non-graphically, outside of synaptic?

~ Eric.

---

### Post by gigoguy on 2007-02-04
This happened to me when I had a custom (and broken) /etc/apt/sources.list
I would recommend restoring your default sources.list

---

