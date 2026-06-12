---
title: "Got some questions and a few installation problems, plz help"
date: 2009-06-28
forum: General Help
---

### Post by ShapeShifter499 on 2009-06-28
Hi everyone, I got a truckload of questions that I'm wondering about and that are driving me nuts! please help.

#1. I was doing some routine updates and my netbook froze, not knowing much what to do I hard booted(holding the power button) my netbook. Now some packages will install but will not configure, why? 

The Packages ```
 python-wnck 
 python-gnomeapplet 
 python-mediaprofiles
 python-evince
 python-gtksourceview
 python-totem-plparser
 python-gnome2-desktop
 python-gnome2-desktop-dbg
 python-evolution
 python-gtop
 python-gnomeprint
 python-gnome2-desktop-dev
 python-gnomedesktop
 python-gnomekeyring
 python-rsvg
 python-metacity
 python-gnome2-extras-dbg
 kubuntu-docs
 screenlets
 python-nautilusburn
 python-bugbuddy
 screenlets-doc

``` 
I ran dpkg --configure -a and got ```
lance@acer-netbook:~$ sudo dpkg --configure -a
[sudo] password for lance: 
Setting up python-wnck (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-wnck (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-gnomeapplet (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gnomeapplet (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-mediaprofiles (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-mediaprofiles (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-evince (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-evince (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-gtksourceview (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gtksourceview (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-totem-plparser (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-totem-plparser (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on python-evince (>= 2.26.0-1ubuntu2); however:
  Package python-evince is not configured yet.
 python-gnome2-desktop depends on python-gnomeapplet (>= 2.26.0-1ubuntu2); however:
  Package python-gnomeapplet is not configured yet.
 python-gnome2-desktop depends on python-gtksourceview (>= 2.26.0-1ubuntu2); however:
  Package python-gtksourceview is not configured yet.
 python-gnome2-desktop depends on python-mediaprofiles (>= 2.26.0-1ubuntu2); however:
  Package python-mediaprofiles is not configured yet.
 python-gnome2-desktop depends on python-totem-plparser (>= 2.26.0-1ubuntu2); however:
  Package python-totem-plparser is not configured yet.
 python-gnome2-desktop depends on python-wnck (>= 2.26.0-1ubuntu2); however:
  Package python-wnck is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop-dbg:
 python-gnome2-desktop-dbg depends on python-gnome2-desktop (= 2.26.0-1ubuntu2); however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing python-gnome2-desktop-dbg (--configure):
 dependency problems - leaving unconfigured
Setting up python-evolution (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-evolution (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-gtop (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gtop (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-gnomeprint (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gnomeprint (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-gnome2-desktop-dev:
 python-gnome2-desktop-dev depends on python-gnome2-desktop (>= 2.26.0-1ubuntu2); however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing python-gnome2-desktop-dev (--configure):
 dependency problems - leaving unconfigured
Setting up python-gnomedesktop (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gnomedesktop (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-gnomekeyring (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gnomekeyring (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-rsvg (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-rsvg (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-metacity (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-metacity (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-gnome2-extras-dbg:
 python-gnome2-extras-dbg depends on python-gnome2-desktop-dbg; however:
  Package python-gnome2-desktop-dbg is not configured yet.
dpkg: error processing python-gnome2-extras-dbg (--configure):
 dependency problems - leaving unconfigured
Setting up kubuntu-docs (9.04.2) ...
ln: target `/usr/share/doc/kde/HTML/en/kubuntu/' is not a directory: No such file or directory
dpkg: error processing kubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of screenlets:
 screenlets depends on python-rsvg | python-gnome2-desktop; however:
  Package python-rsvg is not configured yet.
  Package python-gnome2-desktop is not configured yet.
 screenlets depends on python-wnck | python-gnome2-desktop; however:
  Package python-wnck is not configured yet.
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing screenlets (--configure):
 dependency problems - leaving unconfigured
Setting up python-nautilusburn (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-nautilusburn (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-bugbuddy (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-bugbuddy (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of screenlets-doc:
 screenlets-doc depends on screenlets; however:
  Package screenlets is not configured yet.
dpkg: error processing screenlets-doc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-wnck
 python-gnomeapplet
 python-mediaprofiles
 python-evince
 python-gtksourceview
 python-totem-plparser
 python-gnome2-desktop
 python-gnome2-desktop-dbg
 python-evolution
 python-gtop
 python-gnomeprint
 python-gnome2-desktop-dev
 python-gnomedesktop
 python-gnomekeyring
 python-rsvg
 python-metacity
 python-gnome2-extras-dbg
 kubuntu-docs
 screenlets
 python-nautilusburn
 python-bugbuddy
 screenlets-doc
lance@acer-netbook:~$ 

```

#2. After adding UNR and Ubuntu Studio to my Ubuntu install I upgraded to 9.10 then added Xubuntu, Kubuntu, and Super OS. When I loaded Xfce(Xubuntu) it also loaded the netbook interference from UNR, I thought the interference from UNR wouldn't work in Xfce(Xubuntu) or even load. I guess I was wrong but why? I thought it was gnome only.

#3. After I installed Kubuntu I saw the package Kubuntu-Netbook, I installed it, now how come I don't see any noticable changes after installing Kubuntu-Netbook?

#4. In Kubuntu when I load terminal, terminal starts in the documents folder, does this mean anything? Oh and note just in case it does I have been using the cd code to go to the root.


Thats all of my questions for now.

---

### Post by ShapeShifter499 on 2009-06-28
*bump*

---

