---
title: "Compiz works fine in 9.04, doesn't work in 9.10.  What's the deal?"
date: 2010-03-18
forum: General Help
---

### Post by FunkeyMonk on 2010-03-18
I've got 9.04 and 9.10 both installed on the same machine.  The /home directory is on a separate partition, so both OSes use the same /home.

I can't get Compiz to work at all in 9.10, even though it's been perfectly fine in 9.04.   Is there a backport of some sort that i should install?

I've run Compiz-Check, and I get this:
```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RC410 [Radeon Xpress 200M]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```

Running compiz --replace gives me:
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
```

I've done a lot of googling, and all I can come up with is that the Software rasterizer error usually means that an external monitor/projector is or has been connected and it's at a different resolution or something.   But this is a laptop, and I've never plugged it into an external monitor of any sort.

The fixes I've found all point to editing the xorg.conf file, but of course, Karmic doesn't have an xorg.conf file.  :(

I've tried reinstalling the Compiz files, reinstalled the open-source video drivers, installed/uninstalled fglrx drivers a few times, rebooted dozens of times.   Nothing helps.   Ideas?

---

### Post by dcstar on 2010-03-18
> **FunkeyMonk said:**
> I've got 9.04 and 9.10 both installed on the same machine.  The /home directory is on a separate partition, so both OSes use the same /home.

I can't get Compiz to work at all in 9.10, even though it's been perfectly fine in 9.04.   Is there a backport of some sort that i should install?
........
I've tried reinstalling the Compiz files, reinstalled the open-source video drivers, installed/uninstalled fglrx drivers a few times, rebooted dozens of times.   Nothing helps.   Ideas?

Have a look at the post at the end of this:

[http://superuser.com/questions/63759/no-gui-after-upgrade-to-ubuntu-9-10-boots-to-command-line](http://superuser.com/questions/63759/no-gui-after-upgrade-to-ubuntu-9-10-boots-to-command-line)

---

### Post by ManyuX95 on 2010-03-18
Im not sure if what I guess it is right(if its not, please correct me) but it may be a problem that you have the same configuration of Compiz for both OS

---

### Post by dcstar on 2010-03-18
> **FunkeyMonk said:**
> I've got 9.04 and 9.10 both installed on the same machine.  The /home directory is on a separate partition, so both OSes use the same /home.

I can't get Compiz to work at all in 9.10, even though it's been perfectly fine in 9.04.   Is there a backport of some sort that i should install?
.........

It is also problematic that a shared /home will work correctly between differing releases because of the different Xorg and Gnome versions.

Configuration settings that are valid for 9.04 may break 9.10 and vice-versa.

Start up 9.10** without** the shared /home mounted and then see if things work, if so that that is the problem.

---

### Post by FunkeyMonk on 2010-03-18
> **ManyuX95 said:**
> Im not sure if what I guess it is right(if its not, please correct me) but it may be a problem that you have the same configuration of Compiz for both OS

[QUOTE=dcstar] It is also problematic that a shared /home will work correctly between differing releases because of the different Xorg and Gnome versions.

Configuration settings that are valid for 9.04 may break 9.10 and vice-versa.

Start up 9.10 without the shared /home mounted and then see if things work, if so that that is the problem.[/QUOTE]

Neither of these concerns applies, because GNOME, Xorg, Compix are all stored outside the /home directory.  (Their config files, too.)

But just to be sure, I did create a new user in 9.10, and no dice.

---

### Post by FunkeyMonk on 2010-03-18
> **dcstar said:**
> Have a look at the post at the end of this:

[http://superuser.com/questions/63759/no-gui-after-upgrade-to-ubuntu-9-10-boots-to-command-line](http://superuser.com/questions/63759/no-gui-after-upgrade-to-ubuntu-9-10-boots-to-command-line)

Thanks for the suggestion -- but no luck.  First of all, I'm not sure which post you're referring to.
Second, none of those things in that page have worked for me.  (Yes, I've reconfigured xorg, installed fglrx (and uninstalled it) and tried different users.)

---

### Post by soltanis on 2010-03-18
> **FunkeyMonk said:**
> Neither of these concerns applies, because GNOME, Xorg, Compix are all stored outside the /home directory.  (Their config files, too.)

Gnome I am pretty sure creates a .gnome directory where it stores session data in your home folder. It's pretty common that applications do that (just try ls -al in your home directory to see all of them).

You're right that global configuration files are stored separately, and this obviously doesn't apply to you, but it was worth a try.

---

### Post by 5735guy on 2010-03-20
Ubuntu purge compiz-fusion
[http://ubuntuforums.org/showthread.php?t=546429](http://ubuntuforums.org/showthread.php?t=546429)

Enabling Compiz Fusion On An Ubuntu 9.10 Desktop (NVIDIA Cards)
[http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200](http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200)

ATI Cards

RadeonDriver
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

RadeonXpress
[https://help.ubuntu.com/community/RadeonXpress](https://help.ubuntu.com/community/RadeonXpress)

---

### Post by FunkeyMonk on 2010-03-23
> **5735guy said:**
> Ubuntu purge compiz-fusion
[http://ubuntuforums.org/showthread.php?t=546429](http://ubuntuforums.org/showthread.php?t=546429)


Tried this -- purged all packages with Compiz.  (Also deleted invisible config files.)  Reinstalled fresh Compiz.  Still no luck.

---

