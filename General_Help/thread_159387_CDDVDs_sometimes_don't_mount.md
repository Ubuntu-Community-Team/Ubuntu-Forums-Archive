---
title: "CD/DVDs sometimes don't mount"
date: 2006-04-12
forum: General Help
---

### Post by n0fx on 2006-04-12
I have a strange problem, sometimes when I insert either a CD/DVD (either one) it doesn't mount.  I have to eject the disc and reinsert it to have it autorun or detected by the system.  I checked my /var/log/messages and I get these errors:

Apr 11 18:00:19 localhost kernel: [4410103.483000] VFS: busy inodes on changed media.
Apr 11 18:00:19 localhost kernel: [4410103.485000] VFS: busy inodes on changed media.
Apr 11 18:00:21 localhost kernel: [4410105.489000] VFS: busy inodes on changed media.
Apr 11 18:00:21 localhost kernel: [4410105.491000] VFS: busy inodes on changed media.
Apr 11 18:00:23 localhost kernel: [4410107.495000] VFS: busy inodes on changed media.
Apr 11 18:00:23 localhost kernel: [4410107.497000] VFS: busy inodes 

Sometimes it even causes the system to freeze or hang for a few minutes with those errors before letting me do anything in GNOME. I'm running 2.6.14cK1 (cK patched) with 1 x PATA and 3 x SATA drives (setup with a raid 5 using mdadm).  

Another problem I have is that when I try to erase CDRW/DVDRWs (I have 1 x CDRW and 1 x DVDRW), it doesn't seem to erase.  The only way I can erase the disc is to forcefully umount /dev/cdrom0 and then k3b or gnomebaker will erase them. 

Any help will be appreciated, thanks.

---

### Post by dcstar on 2006-04-13
[QUOTE=n0fx]
.......
Another problem I have is that when I try to erase CDRW/DVDRWs (I have 1 x CDRW and 1 x DVDRW), it doesn't seem to erase.  The only way I can erase the disc is to forcefully umount /dev/cdrom0 and then k3b or gnomebaker will erase them. 

Any help will be appreciated, thanks.[/QUOTE]
I experienced similar problems a while ago, and I (think I) could get around it by installing the pmount package.

---

### Post by n0fx on 2006-04-13
[QUOTE=dcstar]I experienced similar problems a while ago, and I (think I) could get around it by installing the pmount package.[/QUOTE]

Actually, I tried to install the pmount package right now and it says it's already installed, so maybe it's something else that is causing the problem?

---

### Post by dcstar on 2006-04-13
[QUOTE=n0fx]Actually, I tried to install the pmount package right now and it says it's already installed, so maybe it's something else that is causing the problem?[/QUOTE]
Could well be, sometimes you need to run the dmesg command to see what happens when you try to mount/unmount things, give it a try.

---

### Post by n0fx on 2006-04-13
[QUOTE=dcstar]Could well be, sometimes you need to run the dmesg command to see what happens when you try to mount/unmount things, give it a try.[/QUOTE]

I ran the dmesg command and this is what happens:

[4294837.157000] VFS: busy inodes on changed media.
[4294881.217000] VFS: busy inodes on changed media.

Right now, my burning apps froze up, unable to format the disc and I can't even forcefully umount the disc.  The DVDRW drive works perfectly fine with blank DVDs and CDs, just chokes on written DVD+RW discs.

:(

---

