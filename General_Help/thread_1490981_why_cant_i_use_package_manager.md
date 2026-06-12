---
title: "why cant i use package manager"
date: 2010-05-23
forum: General Help
---

### Post by justicejeremy on 2010-05-23
I keep getting this message. I cant use package manger at all . What can I do ?

Errors were encountered while processing:  fglrx E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by shai3421 on 2010-05-23
Try this:
```

sudo export FORCE_ATI_UNINSTALL=/usr/share/ati
sudo apt-get install fglrx
 
```

It's a workaround from one of the bug reports.

---

### Post by hansdown on 2010-05-23
Welcome to the forum justicejeremy.

There are a number of bug reports for this.

[http://www.google.com/search?client=ubuntu&channel=fs&q=Errors+were+encountered+while+processing%3A+fglrx+E%3A+Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+%281%29&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Errors+were+encountered+while+processing%3A+fglrx+E%3A+Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+%281%29&ie=utf-8&oe=utf-8)

Sorry I don't know a fix.

---

### Post by clhsharky on 2010-05-23
HI justicejeremy

What Ubuntu release are you using?
Your ATI Rage card will not work with fglrx drivers if you have 9.04 or newer.

Sharky

---

### Post by justicejeremy on 2010-05-23
Thank you so so much but alas ..nothing . Here is what I get.


jeremy@jeremy-desktop:~$ sudo export FORCE_ATI_UNINSTALL=/usr/share/ati
[sudo] password for jeremy: 
sudo: export: command not found
jeremy@jeremy-desktop:~$ 

I am using the newest  version 10.04 . Will it fix it if I go back to an older version ? I don't want to have to because I have an IPOD touch and I could completely go away from microsoft if I could get these last couple of bugs out ( have a problem with browser size as well).

---

### Post by justicejeremy on 2010-05-23
I do have a ATI Rage card . Ubuntu 10.04

---

### Post by clhsharky on 2010-05-23
HI justicejeremy

Have you tried to synch IPOD in Rhythmbox, should work in Lucid?

fglrx can still be used in Hardy 8.04 with cat 9.3.

Sharky

---

### Post by justicejeremy on 2010-05-24
I didnt have this problem in Karmic until i installed catalyst control center. Id hate to go back to Hardy.. that was actually the first dist. I ever used ! I didnt have many troubles with it I just like the new features of Lucid

---

### Post by ledzepjes on 2010-06-20
I also am getting errors with dpkg, I recently upgraded from 9.10 to 10.04, tried to install ati graphics drivers and control center to be able to get resolutions higher than 1024x768 and use compiz with my ati 4850. I get all kinds of errors, compiz doesn't work, but I have a higher screen resolution now. 

I tried $ sudo export FORCE_ATI_UNINSTALL=/usr/share/ati
and also get "sudo: export: command not found"

When I try to install fglrx:
```
$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  fglrx-amdcccle
The following packages will be upgraded:
  fglrx
1 upgraded, 0 newly installed, 0 to remove and 43 not upgraded.
1 not fully installed or removed.
Need to get 0B/18.2MB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 164590 files and directories currently installed.)
Preparing to replace fglrx 2:8.723.1-0ubuntu3 (using .../fglrx_2%3a8.723.1-0ubuntu4_i386.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu4_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

from another thread I tried:

```
$ dpkg-divert --list
diversion of /bin/sh to /bin/sh.distrib by dash
diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash
diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by dictionaries-common
diversion of /usr/share/dbus-1/services/org.freedesktop.Notifications.service to /usr/share/dbus-1/services/org.freedesktop.Notifications.service.notify-osd by notify-osd
diversion of /usr/bin/screen to /usr/bin/screen.real by screen-profiles
diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx
diversion of /usr/sbin/grub-install to /usr/sbin/grub-install.real by lupin-support
diversion of /usr/lib/gnupg/gpgkeys_curl to /usr/lib/gnupg/gpgkeys_curl.non_curl by gnupg-curl
diversion of /usr/lib/gnupg/gpgkeys_hkp to /usr/lib/gnupg/gpgkeys_hkp.non_curl by gnupg-curl
diversion of /usr/share/gnome-games/pixmaps/slot.svg to /usr/share/gnome-games/pixmaps/slot.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/pixmaps/baize.png to /usr/share/gnome-games/pixmaps/baize.png.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/mahjongg/pixmaps/postmodern.svg to /usr/share/gnome-games/mahjongg/pixmaps/postmodern.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/gnometris/pixmaps/gnometris.svg to /usr/share/gnome-games/gnometris/pixmaps/gnometris.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games-common/cards/gnomangelo_bitmap.svg to /usr/share/gnome-games-common/cards/gnomangelo_bitmap.svg.unbranded by branding-ubuntu

```

and also:

```
$ sudo dpkg --ignore-depends=fglrx --purge fglrx
(Reading database ... 164589 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--purge):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx

```

---

### Post by ledzepjes on 2010-06-20
update, not fixed but:

after reading this forum:
[http://forums.debian.net/viewtopic.php?f=5&t=52486](http://forums.debian.net/viewtopic.php?f=5&t=52486)

and since reading my previous post, the result of "$ dpkg-divert --list" showed "/usr/lib/libGL.so.1.2" was linked with fglrx from the dpkg divert list, (don't ask me what this is)

I ran "$ sudo dpkg-divert --remove /usr/lib/libGL.so.1.2"

before ```
$ dpkg -l '*fglrx*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
iH  fglrx          2:8.723.1-0ubu Video driver for the ATI graphics accelerato
un  fglrx-amdcccle <none>         (no description available)
un  fglrx-control  <none>         (no description available)
un  fglrx-control- <none>         (no description available)
un  fglrx-kernel-s <none>         (no description available)
ii  fglrx-modalias 2:8.723.1-0ubu Identifiers supported by the ATI graphics dr
un  xorg-driver-fg <none>         (no description available)

```

and now I get this when running dpkg -l '*fglrx*'
```
$ dpkg -l '*fglrx*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version           Description
+++-=================-=================-==================================================
un  fglrx             <none>            (no description available)
un  fglrx-amdcccle    <none>            (no description available)
un  fglrx-control     <none>            (no description available)
un  fglrx-control-qt2 <none>            (no description available)
un  fglrx-kernel-sour <none>            (no description available)
ii  fglrx-modaliases  2:8.723.1-0ubuntu Identifiers supported by the ATI graphics driver
un  xorg-driver-fglrx <none>            (no description available)

```

---

### Post by sirced on 2010-06-22
Hi everybody,

shai3421's fix DOES work.

The reason everyone is having problems with it is for some reason sudo export leaves you high and dry. This must mean the bin containing the export script isn't in sudo's path. I don't know why that would be, and don't feel like figuring it out today.

quick fix.
sudo -s  
export FORCE_ATI_UNINSTALL=/usr/share/ati
sh /usr/share/ati/fglrx-uninstall.sh 
apt-get install fglrx
ctrl-d


Why does this work? This tidbit in the error message of apt-get install fglrx:

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run fglrx-uninstall.sh (this is not recommended).

Cheers!
Cedric

---

