---
title: "AutoFsck Problems"
date: 2010-03-26
forum: General Help
---

### Post by cong06 on 2010-03-26
I just found out about [AutoFsck]("http://wiki.ubuntu.com/AutoFsck") and wanted to install it.

I screwed around for a while trying to download the debian file from sourcefourge and finally gave up (I'm behind a squid and apt-cacher server).

So I downloaded source.

Unfortunately on install, it says that zenity and gksu aren't installed:
```

Checking for required programs...

zenity             NOT FOUND
gksu               NOT FOUND
tune2fs            PRESENT
beep               NOT FOUND
GDM                PRESENT
KDM                NOT FOUND

You do not have the required software installed in order to install AutoFsck.  You need to have:
zenity  -  this is a tool for displaying graphical prompts
gksu  -  a tool for requesting your password for root access
tune2fs  -  partition info tool, usually part of package e2fsprogs
beep  -  (optional) this allows AutoFsck to provide an audio prompt
GDM or KDM  -  either one of these display mangers is required

Press enter to exit the installation...

root@kimende-s:~/Desktop/autofsck3.2_generic# aptitude search zenity gksu | grep "^i"
i   gksu                            - graphical frontend to su                  
i   libgksu2-0                      - library providing su and sudo functionalit
i   zenity                          - Display graphical dialog boxes from shell 

```
When they clearly are.

Anyone else have a problem installing AutoFsck from source?

(and why isn't it in the Repo?)

Edit: seems to work fine in my 9.10 UNR, but not in my dekstop: 9.04

---

### Post by oldos2er on 2010-03-26
When compiling source code, you need to install the -dev versions of the packages it requests. **apt-cache search gksu dev** shows libgksu2-dev and libgksu-polkit-dev, so install those, retry ./configure, and repeat the process for any other needed packages.

More info here: [https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by cong06 on 2010-03-27
It's unfortunate that it isn't that easy.
1) libgksu2-dev didn't do it for my desktop.
2) I didn't install libgksu2-dev on my laptop (and it installed there)
3) There is no "configure" script. I don't think it's so much compiling as installing...
4) there is no development "zenity" package:
```

apt-cache search zenity
libui-dialog-perl - UI::Dialog a wrapper for various dialog applications
nautilus-script-collection-svn - Nautilus subversion management scripts
freepops-updater-gnome - GNOME interface for the freepops updater engine
octave-zenity - simple graphical user interfaces using zenity in Octave
ssft - Shell Scripts Frontend Tool
zenity - Display graphical dialog boxes from shell scripts

```

That being said I re-downloaded the package, and ran it.
It worked this time. Who knows?

---

