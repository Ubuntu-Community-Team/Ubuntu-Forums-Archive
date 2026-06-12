---
title: "Ubuntu 10.10 with crashing file system how to run fsck?"
date: 2011-08-09
forum: General Help
---

### Post by llynix on 2011-08-09
I've got a system that has given me problems since day one.  It's my oldest kids computer and she seems to open about twenty tabs in Firefox.  The computer will freeze and she'll manually hold down the switch to reset.  I've instructed her to please stop shutting it down manually but kids never listen.

So anyway the thing reboots into initramfs.  Seems unable to do anything with the hard disk.  Now heres where I run into problems.  In the past I've removed the drive and put it into one of my other Ubuntu boxes then ran fsck.  fsck always recovers the journel quickly and I pop it back in and all is well.

First question or situation if you will.  I have tried left and right to get fsck to work from the livecd.  If I let the livecd boot up and open a terminal fsck /dev/sda1 comes back with device or resource busy.  Apparently the livecd get stuck automounting and causes problems.

I'm really tired of putting this thing in another box.  I tried downloading knoppix but it wouldn't burn off for some reason.  I've tried booting into rescue mode, but that seems to be missing from the livecd these days?

Can I boot into single user mode somehow?  Kill off some process that is causing the resource to be busy?  I'm thinking once I maybe flagged the drive as dirty and had it clean itself on reboot.. will the livecd pick up on that?

ok.. so thats the first situation.. second is upon recently fsck doesn't fix the problem.  The drive recovers just fine, but after using the computer for a short while the drive will somehow magically mount as read only.. and then programs will freeze and shutting down is hard to do.

I've got a full backup of the home directory on this computer and reinstalled from there, but the problem seemed to present itself again.

Any ideas what could be happening?

---

### Post by dcstar on 2011-08-10
> **llynix said:**
> I've got a system that has given me problems since day one.  It's my oldest kids computer and she seems to open about twenty tabs in Firefox.  The computer will freeze and she'll manually hold down the switch to reset.  I've instructed her to please stop shutting it down manually but kids never listen.

So anyway the thing reboots into initramfs.  Seems unable to do anything with the hard disk.  Now heres where I run into problems.  In the past I've removed the drive and put it into one of my other Ubuntu boxes then ran fsck.  fsck always recovers the journel quickly and I pop it back in and all is well.

First question or situation if you will.  I have tried left and right to get fsck to work from the livecd. ** If I let the livecd boot up and open a terminal fsck /dev/sda1 comes back with device or resource busy.**  Apparently the livecd get stuck automounting and causes problems.

........

```
**sudo** fsck /dev/sda1
```

---

### Post by llynix on 2011-08-10
> **dcstar said:**
> ```
**sudo** fsck /dev/sda1
```

Thank you for the quick reply, but I wasn't born yesterday really.

I actually know quite a lot about this stuff.  This computer has just been weird.

---

### Post by llynix on 2011-08-11
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

This is what I get when I try from the livecd.

---

### Post by llynix on 2011-08-11
In addition the livecd will not shut down.  It hangs forever and you need to hit the power button.

I got knoppix to burn off and fixed it up with their livecd using knoppix 2 for the boot since X was all messed up upon loading.

root@Microknoppix:/# fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda1 recovering journal
Clearing orphaned inode 393249 (uid=1000, gid=1000, mode=0100600, size=8192)
/dev/sda1: clean, 166904/4685824 files, 4911463/18730240 blocks


Now the computer is running fine.. until that is the kid gets to it again.  I've instructed her to tell me if anything goes wrong and to not shut down the computer at all so I can further troubleshoot.

---

### Post by llynix on 2011-08-12
daughter tried to login to her computer but it didn't successfully load X.  By using CNTRL-ALT-F3 I was able to drop to a prompt and log-in.  I tried echo '' > blah in her home directory and got:

-bash: blah: Read-only file system

I tried looking into logs to see if I could spot anything.. but didn't see anything in /var/log/* that was out of the ordinary or pertaining to drive failure.  Is there a way to turn on more logging?

Since the drive is read only I can run fsck on it so I did so:

/dev/sda1: recovering journal
Clearning orphaned inode 393243 (uid=1000, gid=1000, mode=0100600, size=8192)

Finally I did a sudo shutdown -r now to see if the problem was somewhat solved.

I did find a PM failed to resume... perhaps ACPI is causing problems.

The computer auto-logged in and came to the desktop.  I looked into power settings and the system was set to never idle.  I then went to look into the screensaver and noticed the computer started becoming unresponsive.  The window for appearance preferences came up, but is white and blank.  Same with a terminal window.

I then hit CNTRL-ALT-F3 again and got to a prompt.

echo '' > blah
-bash: blah: Read-only file system

I'm going round and round here.  Linux virus?

ok.. again I'm read only so I try again:
Same exact thing running fsck.. except this time it's orphaned inode 393252.

:(

Any ideas?

---

### Post by llynix on 2011-08-29
I ended up running a slew of drive tests on the computer.  All turned up just fine.  Finally I ran memtest86 on it.  It immediately turned up memory problems.  Turns out one of the slots on the motherboard wasn't playing nice.  I've RMA'd the unit.

---

