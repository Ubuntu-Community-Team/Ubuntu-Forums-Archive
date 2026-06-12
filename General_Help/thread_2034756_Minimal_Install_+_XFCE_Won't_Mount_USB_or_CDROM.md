---
title: "Minimal Install + XFCE Won't Mount USB or CDROM"
date: 2012-07-28
forum: General Help
---

### Post by Spiralagnus on 2012-07-28
I know this question has been addressed before on this board, but I was unable to find an answer that worked for me after extensive searching.

I just did a minimal install of Ubuntu and XFCE (not Xubuntu, just minimal Ubuntu, with only the packages xorg, gdm, xfce and thunar-volman installed).  I cannot get Ubuntu to automount my CDROM drives or USB drives.  It recognizes the USB drives with fdisk:

```
sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000683b1

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  2914025471  1457011712   83  Linux
/dev/sda2      2914027518  2930276351     8124417    5  Extended
/dev/sda5      2914027520  2930276351     8124416   82  Linux swap / Solaris

Disk /dev/sdb: 975 MB, 975175680 bytes
25 heads, 24 sectors/track, 3174 cylinders, total 1904640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1512     1904639      951564    6  FAT16

```(sdb1 is the USB drive), and it recognizes both with blkid:

```
sudo ./blkid

/dev/sda1: UUID="6cef6eb5-6051-407b-a42a-85de8b90dc6c" TYPE="ext4" 
/dev/sda5: UUID="0f789202-cdc1-42b4-9038-a215da211cdb" TYPE="swap" 
/dev/sr0: LABEL="CDROM" TYPE="iso9660" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="PENDRIVE" UUID="0C90-C33B" TYPE="vfat"
```However, neither drive appears in fstab or mtab, although from reading some of the other threads, it's not necessary for them to do so.  I was able to mount the drives doing a manual mount:

```

sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```This is how I mounted the USB drive.  But when I did this, the files were read-only, sudo wouldn't change permissions on the directory, and when I restarted the machine and plugged my USB drive again, it didn't show up in /media/sdb1

"Enable Volume Management" is checked under File Manager Preferences -> Advanced, but the drives still refuse to mount.  Is there something else I need to install?  Some setting that I need to change?

Thanks in advance to the community for their help.

---

### Post by Scott Goodgame on 2012-07-28
There are several options available to you described in the link below...
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)


Google is your friend.

---

### Post by Spiralagnus on 2012-07-28
> **Scott Goodgame said:**
> There are several options available to you described in the link below...
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)


Google is your friend.

Thank you.  I'll look at this more closely.  I spent an extensive amount of time on Google but didn't come up with this.

Since my last post, I edited my fstab file and added this line:

```
UUID=0C90-C33B /home/xxx/usb1 vfat defaults,umask=000,errors=continue 0 0 
```

Now when I plug the drive in, it mounts so long as I run

```
sudo mount -a
```

and the umask makes the mount drive writeable, so I can transfer files to it.  However, I have to re-run this command every time I plug the drive in.  The consensus seems to be that automount isn't something you can do in a minimal install (you need Gnome tools or something similar), but I'll keep looking into it.  Any other suggestions would be welcome.

---

### Post by Scott Goodgame on 2012-07-29
You are using XFCE, so Thunar is your file manager, right?
Did you go to Edit -> Prefs _> File Manager Prefs and enable (and configue) volume managment?

---

### Post by Spiralagnus on 2012-07-29
> **Scott Goodgame said:**
> You are using XFCE, so Thunar is your file manager, right?
Did you go to Edit -> Prefs _> File Manager Prefs and enable (and configue) volume managment?

As I stated in the original post, I've made these changes.  Here's how things look:

[IMG]http://i45.tinypic.com/34hz1qu.png[/IMG]

[IMG]http://i45.tinypic.com/w8xfk2.png[/IMG]

---

### Post by miegiel on 2012-07-29
Not the solution you want, but I hope it helps you anyway.

I don't automount "disks" in XFCE (on debian), but use the *mount devices* item in the XFCE panel. To add it, right click the panel > etc. > etc.

---

### Post by Spiralagnus on 2012-07-29
> **miegiel said:**
> Not the solution you want, but I hope it helps you anyway.

I don't automount "disks" in XFCE (on debian), but use the *mount devices* item in the XFCE panel. To add it, right click the panel > etc. > etc.

I'm afraid I don't follow.  Would you please be a little more specific about where I should click?

There's been some progress on this issue.  After installing gvfs and dbus

```
sudo apt-get install gvfs dbus --no-install-recommends
```icons now appear on my desktop when I plug in a USB drive or insert a CD into the CD-ROM.  However, I now get the following error when I double-click on the icon to open it:

```
Not Authorized: 
GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: 
The name org.freedesktop.PolicyKit1 was not 
provided by any .service files
```[IMG]http://i50.tinypic.com/2h563gy.png[/IMG]

I can get the files to appear only if I go into the terminal and do a manual mount. Any suggestions would be most appreciated.

---

### Post by Spiralagnus on 2012-07-29
Further progress.  I was able to automount the thumb drive by editing fstab with the following line:

```
UUID=0C90-C33B /media/usb vfat user 0 0
```

The problem is that the UUID applies to that particular device, so if I want to plug in a different USB device, I have to edit fstab again.  How do I get my minimal XFCE Ubuntu to accept and automount any USB device automatically, like Windows does?

---

### Post by miegiel on 2012-07-29
> **Spiralagnus said:**
> I'm afraid I don't follow.  Would you please be a little more specific about where I should click?

If you right click on the panel (that's what it's called in XFCE, sometimes people call it dock or taskbar) where your main menu, running programs and notification area (aka system tray) are. And click *panel* > *panel preference* and go to the *items* tab. You can add more items to the panel (and rearrange them). There is a *mount devices* item that I use to mount devices.

---

### Post by Spiralagnus on 2012-07-29
> **miegiel said:**
> If you right click on the panel (that's what it's called in XFCE, sometimes people call it dock or taskbar) where your main menu, running programs and notification area (aka system tray) are. And click *panel* > *panel preference* and go to the *items* tab. You can add more items to the panel (and rearrange them). There is a *mount devices* item that I use to mount devices.

Okay, I follow now, but there isn't a "Mount Devices" option in list of items:

[IMG]http://i46.tinypic.com/2u6poav.png[/IMG]

Bear in mind that I'm running minimal Ubuntu with an XFCE interface.  Is there something I need to install to make this option appear?

---

### Post by miegiel on 2012-07-29
> **Spiralagnus said:**
> Further progress.  I was able to automount the thumb drive by editing fstab with the following line:

```
UUID=0C90-C33B /media/usb vfat user 0 0
```

The problem is that the UUID applies to that particular device, so if I want to plug in a different USB device, I have to edit fstab again.  How do I get my minimal XFCE Ubuntu to accept and automount any USB device automatically, like Windows does?

I just checked my */etc/fstab* and it has this line:
```
/dev/sdb1       /media/usb0     auto    rw,user,noauto  0       0
```
I only have one disk, so */dev/sdb1* will always be the first partition of the inserted (second) disk. It might only work for external disks though and not for CD/DVD's (I never use them :D).

---

### Post by miegiel on 2012-07-29
> **Spiralagnus said:**
> Okay, I follow now, but there isn't a "Mount Devices" option in list of items:

... snip pic ...

Bear in mind that I'm running minimal Ubuntu with an XFCE interface.  Is there something I need to install to make this option appear?

Maybe you didn't install that part of XFCE. To install from the terminal:
```
sudo apt-get install xfce4-mount-plugin
```
(99% sure that's the right package)

Make that 100% sure [http://packages.ubuntu.com/precise/xfce4-mount-plugin](http://packages.ubuntu.com/precise/xfce4-mount-plugin)

---

### Post by Spiralagnus on 2012-07-29
> **miegiel said:**
> Maybe you didn't install that part of XFCE. To install from the terminal:
```
sudo apt-get install xfce4-mount-plugin
```(99% sure that's the right package)

Thanks.  That gave me what I need.

> **miegiel said:**
> I just checked my */etc/fstab* and it has this line:
```
/dev/sdb1       /media/usb0     auto    rw,user,noauto  0       0
```I only have one disk, so */dev/sdb1* will always be the first partition of the inserted (second) disk. It might only work for external disks though and not for CD/DVD's (I never use them :D).

Yeah, I've been exploring that route, but it only really works if you're going to have a single device plugged in at once.  The problem is that I have multiple USB devices plugged in at any given time. 

I think it would help if I set up auto unmount as well.  Any suggestions on how to do this?  Please let me know.

---

### Post by miegiel on 2012-07-29
> **Spiralagnus said:**
> Thanks.  That gave me what I need.



Yeah, I've been exploring that route, but it only really works if you're going to have a single device plugged in at once.  The problem is that I have multiple USB devices plugged in at any given time. 

For 3 devices this might work (assuming you have only 1 hard drive too):
```
/dev/sdb1       /media/external0     auto    rw,user,noauto  0       0
/dev/sdc1       /media/external1     auto    rw,user,noauto  0       0
/dev/sdd1       /media/external2     auto    rw,user,noauto  0       0
```
You might also need to create the directories in */media/*
```
sudo mkdir /media/external0 /media/external1 /media/external2
```
and change the ownership from root to your user account.
```
sudo chown [COLOR="Red"]user[/COLOR]:[COLOR="Red"]user[/COLOR] /media/externa*
```
where [COLOR="Red"]user[/COLOR] is your user name.
> I think it would help if I set up auto unmount as well.  Any suggestions on how to do this?  Please let me know.
I'm one of those people that always disables automount. :D

---

### Post by Spiralagnus on 2012-07-29
> **miegiel said:**
> For 3 devices this might work (assuming you have only 1 hard drive too):
```
/dev/sdb1       /media/external0     auto    rw,user,noauto  0       0
/dev/sdc1       /media/external1     auto    rw,user,noauto  0       0
/dev/sdd1       /media/external2     auto    rw,user,noauto  0       0
```You might also need to create the directories in */media/*
```
sudo mkdir /media/external0 /media/external1 /media/external2
```and change the ownership from root to your user account.
```
sudo chown [COLOR=Red]user[/COLOR]:[COLOR=Red]user[/COLOR] /media/externa*
```where [COLOR=Red]user[/COLOR] is your user name.

I'm one of those people that always disables automount. :D

Done. I have mount working almost perfectly, but unmount's a little trickier.  Here's the error message I get when I right-click on a drive and select "Eject Volume":

[IMG]http://i49.tinypic.com/2nvdbk.png[/IMG]

Interestingly, the drive unmounts anyway, but I'm not sure where this error is coming from.  Any ideas?

And why disable automount?  Doesn't that save you a step when plugging in drives?

---

### Post by miegiel on 2012-07-29
> **Spiralagnus said:**
> Done. I have mount working almost perfectly, but unmount's a little trickier.  Here's the error message I get when I right-click on a drive and select "Eject Volume":

... snip pic ...

Interestingly, the drive unmounts anyway, but I'm not sure where this error is coming from.  Any ideas?
It might be some mechanism that allows you to do stuff (like unmounting) as root without entering a root/superuser password. But I'm just guessing.

> And why disable automount?  Doesn't that save you a step when plugging in drives?
I'm a control freak :D ... well, that and I almost always have a drive connected to my laptop that doesn't need to be mounted most of the time. If it's not mounted it's harder to break it by accident ;)

---

### Post by Spiralagnus on 2012-07-29
Okay, so it turns out that when I right-click and select "Eject Volume", I'm able to unmount it but not eject it (since only root can eject).  However, there's no "Unmount Volume" option when I right-click.  Should there be, and if so, how do I add it?

---

### Post by miegiel on 2012-07-29
> **Spiralagnus said:**
> Okay, so it turns out that when I right-click and select "Eject Volume", I'm able to unmount it but not eject it (since only root can eject).  However, there's no "Unmount Volume" option when I right-click.  Should there be, and if so, how do I add it?

If you search for ["org.freedesktop.PolicyKit1"]("https://duckduckgo.com/?q="org.freedesktop.PolicyKit1"") you'll find a lot of bugs (I even see a result linking to ubuntu lucid when it was still in development). I'm just guessing again, but there's a good chance that in the way you installed XFCE you created the same or similar problem on your machine. You might be missing another packages XFCE uses for this, or it might be a configuration setting in your */home/user/* directory or (more likely) somewhere in the */var/* directories

In any case, I only see *mount volume* and *eject volume* in my filebrowser too. So that's "normal".

---

### Post by Spiralagnus on 2012-07-29
> **miegiel said:**
> If you search for ["org.freedesktop.PolicyKit1"]("https://duckduckgo.com/?q=%22org.freedesktop.PolicyKit1%22") you'll find a lot of bugs (I even see a result linking to ubuntu lucid when it was still in development). I'm just guessing again, but there's a good chance that in the way you installed XFCE you created the same or similar problem on your machine. You might be missing another packages XFCE uses for this, or it might be a configuration setting in your */home/user/* directory or (more likely) somewhere in the */var/* directories

In any case, I only see *mount volume* and *eject volume* in my filebrowser too. So that's "normal".

So what happens when you right-click on a mounted USB drive and select "Eject Volume"?  Do you get an error message, or does the drive eject successfully?

---

### Post by miegiel on 2012-07-29
> **Spiralagnus said:**
> So what happens when you right-click on a mounted USB drive and select "Eject Volume"?  Do you get an error message, or does the drive eject successfully?

It unmounts an disappears from the file browser and I can't mount it again until I've unplugged and replugged it. No errors, no message.

---

### Post by Spiralagnus on 2012-07-29
So I went ahead and did an install of policykit-1.  That seems to have made progress.  At least, the aforementioned error message has gone away, but I'm still getting a weird fail message:

```
Not Authorized: 
GDBus.Error:org.freedesktop.DBus.Error.TimedOut: 
Activation of org.freedesktop.PolicyKit1 timed out
```

I think the problem is that as I was setting up my OS, I kept installing everything with the 

```
--no-install-recommends
```

flag, since I thought that would pour a bunch of junk onto my system that I didn't need, and my goal was to make this as tight a build as possible.  The result is that I installed a lot of stuff without the needed dependencies, so I ran into all sorts of problems as a result.  There's probably a lesson here somewhere.  :p

---

### Post by Spiralagnus on 2012-07-29
...aaaand restarting resolved that error.  Okay, everything seems to be working now.  I can right-click on the drive -> Eject Volume, and the icon disappears with no errors.  I'll mark this as SOLVED.

For the record, is there a way to tell Ubuntu "analyze this piece of software I installed, look for any dependencies that were supposed to be installed with it but weren't, and install those dependencies"?  I'd like to avoid any other potential problems that may have resulted from my overuse of the 

```
--no-install-recommends
```

flag.

---

### Post by miegiel on 2012-07-29
Whenever I want to know more about a package, like dependencies, I do:
```
aptitude show *packagename*
```
You'll need to have aptitude installed though :P

Good to see it's fixed.

---

### Post by Spiralagnus on 2012-07-30
Thank you everybody for all of your help.

---

### Post by jlacroix on 2012-08-03
I'm having this issue right now, wasn't sure if I should start a new topic because this one already exists. I have Ubuntu Server, with XFCE installed as a GUI for when I need it. I cannot mount my USB drives, I get the "not authorized" error. I cannot back up my server because it cannot mount anything. I've tried everything in this topic.

The funny thing is, it was working fine up until this week. :(

---

### Post by jlacroix on 2012-08-03
> **jlacroix said:**
> I'm having this issue right now, wasn't sure if I should start a new topic because this one already exists. I have Ubuntu Server, with XFCE installed as a GUI for when I need it. I cannot mount my USB drives, I get the "not authorized" error. I cannot back up my server because it cannot mount anything. I've tried everything in this topic.

The funny thing is, it was working fine up until this week. :(
Nevermind, I found it. 

I had to edit:
/usr/share/polkit-1/actions/org.freedesktop.udisks.policy

I changed “allowed_any” and “allow_inactive” to “yes”.

---

