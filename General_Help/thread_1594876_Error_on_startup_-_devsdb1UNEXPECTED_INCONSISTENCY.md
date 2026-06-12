---
title: "Error on startup - /dev/sdb1:UNEXPECTED INCONSISTENCY"
date: 2010-10-12
forum: General Help
---

### Post by t0p on 2010-10-12
I'm running Eeebuntu 3 (basically Jaunty) on my EeePC 701.  Just lately I've been having the following problem (and no, I don't know what I did to trigger this):

When booting the netbook, I get this error message:

```

/dev/sdb1: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY (ie without -a or -p options)
fsck died with exit status 4.
Checking drive /deb/sdb1: 92% (stage 4/5, 3/31
* file system check failed
A log is being saved in /var/lock/fsck/checkfs if that location is writable.
Please repair the file system manually.
* A maintenance shell will now be started.  CONTROL-D will terminate this shell and resume system boot.
Give root password for maintenance, or type CONTROL-D to continue:

```

Luckily, I had already set a root password.  So I typed it in, then ran FSCK.
A number of operations were suggested, I hit "y" for each one.  Then got the output:

```

/dev/sda1:
*****REBOOT LINUX*****
/dev/sda1:
181711/488640 files (2.2% non-contiguous), 853514/975940 blocks

```

I rebooted, by typing in

```

shutdown -P now

```

This leads to a terminal login window.  Then the following message pops up:

```

Failed to start X server (your graphical interface).  It is likely that it is not set up properly.  Would you like to view the X server output to diagnose problem?

```

I selected "Yes", then got this:

```

mkdir: cannot create directory `/tmp/dexconf-tmp-3857': Invalid argument.
Failsafe Dexconf: error.creation of temporary work [?] directory.
"/tmp/dexconf-tmp-3837" failed.
Warning: Could not generate /etc/X11/xorg.conf failsafe for vesa driver

```

I selected <exit>; then

```

The X server is now disabled.  Restart gdm when it is configured correctly.

```

I don't know how to configure the X server correctly.  But the only option now is to hit <OK>, which took me back to a terminal (text) login.  So, I logged in.

```

No directory, logging in with HOME=/
-bash: cannot create temp file here document: Invalid argument.

```

I now closed it down with

```

sudo shutdown -P now
```

and the computer closes down.  But when I restart, it takes me back to the **/dev/sdb1: UNEXPECTED INCONSISTENCY** again...

Curiously, if I don't input the root password but hit CONTROL-D instead, Ubuntu loads *apparently* fine.

Any ideas?

---

### Post by searchfgold6789 on 2010-10-12
Try this:

[LIST=1]
[*]Go into a live desktop.
[*]Open a terminal.
[*]Type this in: ```
sudo mount /dev/sdXX /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
```
[*]type ```
 sudo fsck 
```
[*]see what happens and post back.
[/LIST]
Hope this helps!
 - search

---

