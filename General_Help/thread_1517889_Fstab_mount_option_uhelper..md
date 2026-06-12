---
title: "Fstab mount option uhelper."
date: 2010-06-25
forum: General Help
---

### Post by supergrav on 2010-06-25
I was just curious to know what's the effect of uhelper=udisks option in fstab file is? Except udisks what can i use?

---

### Post by supergrav on 2010-06-29
bump...

---

### Post by blausand on 2010-11-07
Bump also. uhelper=hal? man mount says nothing. man fstab says nothing. ubuntu-specific parameter? unmounting parameter? can this be crucial?
Please sb. link to official doc. Thank you.

---

### Post by Colin Keenan on 2011-03-22
I don't know the answer to what you are specifically asking, but found this thread while trying to figure out how to mount the stuff in the "Places" dropdown menu when I log in without having to click on "Places' and then each disk that I wanted to mount.

Your thread doesn't answer that, of course, but in case anyone else reading this wants to be able to mount the "Places" stuff when they login, here's what works perfectly for me.  Don't even mess around with etc/fstab.  Instead add the following to your Startup Applications

udisks --mount /dev/[fill in the device]

So, for example, if you have a second drive in your computer and you want to mount the first partition, that is /dev/sdb1, and you would mount it with

udisks --mount /dev/sdb1

and do NOT use "sudo".

To make this happen whenever you login, just goto

System -> Preferences -> Startup Applications
 [+Add] 
Name: Mount My 2nd Drive (or whatever)
Command: udisks --mount /dev/sdb1

It's that easy.  No need to edit etc/fstab and put in a bunch of options you don't understand.

---

### Post by rachel.greenham on 2011-06-06
> **Colin Keenan said:**
> I don't know the answer to what you are specifically asking, but found this thread while trying to figure out how to mount the stuff in the "Places" dropdown menu when I log in without having to click on "Places' and then each disk that I wanted to mount.

...snip...

It's that easy.  No need to edit etc/fstab and put in a bunch of options you don't understand.

That said, doing it the fstab way was if anything easier, and has the benefit that the mount happens during the boot sequence rather than later, when you log in. This mattered to me because I was having a problem where mediatomb (DLNA server) was emptying itself of content on boot when it started up and found the location of all its media files was missing, because it was all on a Vault RAID array that only got mounted manually after booting. Merely supplying the volume at that later point wasn't helpful: mediatomb was still empty.

The shortcut to adding "Places" mount points to /etc/fstab lies in the fact that in a running system, they show up in the dynamically-created file /etc/mtab, which uses the same format as /etc/fstab.

So in my case, I had my RAID array manually mounted on /media/Vault. I could do this:

```

sudo su -
grep Vault /etc/mtab >> /etc/fstab
reboot

```

Translated: 1: Become root. 2: Find the line in /etc/mtab with "Vault" in it (ie: the volume label) and append it to the end of /etc/fstab. 3: Reboot.

In fact the reboot isn't even necessary. You could manually dismount the volume, then "mount -a" automatically mounts everything in /etc/fstab that isn't already mounted.

The mount point still even shows up in Places/Unity Launcher/Desktop.

I'm not sure this worked in the past, I'm sure I would have tried it last time I wanted to mount these things at boot *and* (partly for reasons of vanity and convenience) wanted to keep the drive icons. But it does appear to work on Natty at least.

It's *possible* the uhelper=udisks option (which shows up in the line in /etc/mtab) is part of why that works.

---

### Post by ezander on 2012-12-02
The answer is in 'man umount' (uhelper means something like 'umount helper'). If you have specified uhelper=foo in fstab, then when you umount the device, /sbin/umount.foo is invoked. To quote from the manpage:

> The syntax of external umount helpers is:

```
/sbin/umount.<suffix> {dir|device} [-nlfvr] [-t type.subtype]
```

where the <suffix> is filesystem type or a value from "uhelper=" or "helper=" mtab option.  The -t option is used  for  filesystems with subtypes support (for example /sbin/mount.fuse -t fuse.sshfs).

The  uhelper=  (unprivileged umount helper) is possible to use when non-root user wants to umount a mountpoint which is not defined in the /etc/fstab file (e.g devices mounted by udisk).

The helper= mount option redirects all umount requests to the /sbin/umount.<helper> independently on UID.


If you specify the wrong uhelper, strange things may happen, although if the helper doesn't exist, it's not so bad (you don't even get an error message). If you don't want the helper to execute, use umount -i.

---

### Post by oldos2er on 2012-12-02
Closed. Please don't bump old threads.

---

