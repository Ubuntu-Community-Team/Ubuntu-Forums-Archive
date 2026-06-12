---
title: "Updater damaged by my haste."
date: 2012-05-20
forum: General Help
---

### Post by Michael Grabbe on 2012-05-20
I recently installed Precise Pangolin and it worked ok, but I missed the UI in 11.04. Today, I was reading Linux User & Developer and thought I'd try installing some other desktops. Gnome went ok. Then I stepped thru the process of installing MATE - saw some strange behavior in the terminal, and finally when I restarted I noticed a red circle with a white line thru it displayed at the top of my screen. I should have read the section of the article before I tried this as MATE was only for Ubuntu v11.10. Bad news for me! Clicking on the red circle displayed a message to right click... and run update manager.  Update manager won't run with this error.  I saw an error E:Malformed line 59 in source list /etc/apt/sources.list (dist parse).  How do I fix this?

---

### Post by wilee-nilee on 2012-05-20
> **Michael Grabbe said:**
> I recently installed Precise Pangolin and it worked ok, but I missed the UI in 11.04. Today, I was reading Linux User & Developer and thought I'd try installing some other desktops. Gnome went ok. Then I stepped thru the process of installing MATE - saw some strange behavior in the terminal, and finally when I restarted I noticed a red circle with a white line thru it displayed at the top of my screen. I should have read the section of the article before I tried this as MATE was only for Ubuntu v11.10. Bad news for me! Clicking on the red circle displayed a message to right click... and run update manager.  Update manager won't run with this error.  I saw an error E:Malformed line 59 in source list /etc/apt/sources.list (dist parse).  How do I fix this?


Post all the text you get from running cat /etc/apt/sources.list in a terminal.

I think mate can be run in 12.04, not sure though, this error is just in the repo list.

---

### Post by miegiel on 2012-05-20
I'm not sure but there might be a line referencing a old release in your */etc/apt/sources.list*.

---

### Post by sikander3786 on 2012-05-20
> **wilee-nilee said:**
> I think mate can be run in 12.04, not sure though...

Yeah, it is available for Precise:

[http://www.tuxgarage.com/2012/04/install-mate-in-ubuntu-precise-oneiric.html](http://www.tuxgarage.com/2012/04/install-mate-in-ubuntu-precise-oneiric.html)

And in fact, it can be run with Compiz also:

[http://www.tuxgarage.com/2012/05/run-mate-with-compiz-in-ubuntu.html](http://www.tuxgarage.com/2012/05/run-mate-with-compiz-in-ubuntu.html)

---

### Post by Michael Grabbe on 2012-05-20
Below is what I see when opening the file in a text editor.  I see references to "Oneiric".  Is it as simple as correcting those references?  I tried to copy from the terminal program but could not...


# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb [http://packages.mate-desktop.org/repo/ubuntuoneiric](http://packages.mate-desktop.org/repo/ubuntuoneiric) main
deb-src [http://packages.mate-desktop.org/repo/ubuntuoneiric](http://packages.mate-desktop.org/repo/ubuntuoneiric) main
deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main
deb-src [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main

---

### Post by wilee-nilee on 2012-05-20
Line 59 and 60 is oneiric you are running precise.

deb [http://packages.mate-desktop.org/repo/ubuntuoneiric](http://packages.mate-desktop.org/repo/ubuntuoneiric) main
deb-src [http://packages.mate-desktop.org/repo/ubuntuoneiric](http://packages.mate-desktop.org/repo/ubuntuoneiric) main

I would just open the source manager with.

```
sudo gedit /etc/apt/sources.list
```You are now in edit mode and sub precise for oneiric save it and run in the terminal.

```
sudo update-grub
```That should fix it, I assume that just the name change will fix this should I would think.

While in there as well you have the maverick stuff locked off with a # but if me I would remove it to simplify the list.

---

### Post by Michael Grabbe on 2012-05-20
Did the edit - replaced oneiric with precise, then ran update-grub. Apparently the machine did not like it at all. After I tried to restart,I got the flashing cursor on the screen. Looks like I'll be reloading...

---

### Post by wilee-nilee on 2012-05-20
> **Michael Grabbe said:**
> Did the edit - replaced oneiric with precise, then ran update-grub. Apparently the machine did not like it at all. After I tried to restart,I got the flashing cursor on the screen. Looks like I'll be reloading...

You can if you want but that change would not have a cause and effect on that reboot. Probably fixable if you have the patience. :)

---

### Post by Michael Grabbe on 2012-05-20
Well I don't what what actually caused the machine to misbehave, but here's what I ended up doing. Tried to boot from 12.04 Beta CD, and it wouldn't. Pulled power and discharged caps in system. Reset BIOS to boot from CD (again) and inserted the magazines CD. Saw a menu with a choice of booting from hard-drive and selected that. System booted up normally.  Then followed instructions from link provided by Sikander3786. All seems to be OK now. Thank you all! :-)

---

### Post by wilee-nilee on 2012-05-20
> **Michael Grabbe said:**
> Well I don't what what actually caused the machine to misbehave, but here's what I ended up doing. Tried to boot from 12.04 Beta CD, and it wouldn't. Pulled power and discharged caps in system. Reset BIOS to boot from CD (again) and inserted the magazines CD. Saw a menu with a choice of booting from hard-drive and selected that. System booted up normally.  Then followed instructions from link provided by Sikander3786. All seems to be OK now. Thank you all! :-)

Cool, have fun. :)

---

