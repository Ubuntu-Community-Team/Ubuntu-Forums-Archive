---
title: "Mount of root file system failed"
date: 2010-02-23
forum: General Help
---

### Post by KernelKnight on 2010-02-23
I have had this problem since yesterday, I've looked around at previous archives, but I can't seem to find anything that works. 
When I boot up, the screen gives me the following prompt:

```
Mount of root filesystem failed.
A maintenance shel will now be started.
CONTROL-D will terminate this shell and reboot the system.
Give root password for maintenance:
(or type Control-D to continue);_
```I have tried looking at the fstab file, and also tried to use the fsck command. 
This is what I get with the fsck command on the / partition:

```
root@mylaptop:~#fsck /dev/sda1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? 
```Naturally I typed "n" to that prompt and unmounted /dev/sda1

```
root@mylaptop:~#umount /dev/sda1
```And then tried it again.

```
root@mylaptop:~#fsck /dev/sda1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1: clean, 244628/625856 files, 1444516/2500107 blocks


```When I use CTRL+D, making the system reboot I get this befor it turns off

```
umount: /dev: device is busy
        (In some cases useful info about processes that use
        the device is found by lsof(8) or fuser(1))


```Thank you in advance.

---

### Post by KernelKnight on 2010-02-23
If it helps. I'm not on dual boot. That seemed to make problems for some people. Karmic is the only system I'm running on this machine.

---

### Post by dabl on 2010-02-23
You need to boot a Live CD, and run fsck from that session, on the partition where your OS is installed.  That way it won't be mounted.

---

### Post by KernelKnight on 2010-02-23
Ok, I just did that now it says:

```
ubuntu@ubuntu:~$sudo fsck /dev/sda1
fsck from util-linux-ng 2.16
e2fsck1.41.9(22-Aug-2009)
/dev/sda: clean, 244628/625856 files, 1444516/2500107
```I come back to boot up and the prompt is the same.

---

### Post by dabl on 2010-02-23
Let's have a look at the output of these:

```
sudo blkid
```

```
cat /etc/fstab
```

---

### Post by KernelKnight on 2010-02-23
blkid:

```
/dev/sda1: UUID="e56572ac-0316-422d-b6e8-bfa6c4fb2d5d" TYPE="ext4"
/dev/sda5: UUID="4898688b-0843-43a3-ab6f-ae283b39e870" TYPE="swap"
/dev/sda6: UUID="274d070d-0c44-497e-ab20-6e9a2409559b" TYPE="ext4"

```cat /etc/fstab
```
#/etc/fstab: static file system information
#Use 'blkid -o value -s UUID' to pring the universally unique identifier
#for a device; this may be used with UUID= as a more robust way to name 
#devices that works even if disks are added and removed. See fstab(5).
#
# <file system>   <mount point> <type> <options> <dump> <pass>
proc        /proc         proc          defaults          0          0
# / was on /dev/sda1 during installation
UUID=e56572ac-0316-422d-b6e8-bfa6c4fb2d5d   /    ext4     errors=remount-ro 0    1
# /home was on /dev/sda6 during installation
UUID=274d070d-0c44-497e-ab20-6e9a2409559b  /home    ext4    defaults 0     2
#swap was on /dev/sda5 during installation
UUID=4898688b-0843-43a3-ab6f-ae283b39e870   none     swap    sw     0     0
/dev/scd0         /media/cdrom0        udf,iso9660  user,noauto,exec,utf   0     0

```

---

### Post by dabl on 2010-02-23
Hmmm.  I don't see anything obviously wrong.  OK, let's give fsck one more shot, but this time (from booted Live CD):
```

sudo fsck -fpv /dev/sda1
```

and then do it again on /dev/sda6.

Assuming it shows no filesystem errors, I would recommend (while still in your Live CD session) adding some mount options to your /etc/fstab file as follows:

for the root "/" filesystem:

UUID=e56572ac-0316-422d-b6e8-bfa6c4fb2d5d   /    ext4     errors=remount-ro[COLOR="Red"]**,noatime**[/COLOR] 0    1

for the /home filesystem:

UUID=274d070d-0c44-497e-ab20-6e9a2409559b  /home    ext4    [COLOR="Red"]**auto,users,rw,exec,noatime**[/COLOR] 0     2

Then reboot your installed system, and let's see what you get.  (I'll cross my fingers ....).

---

### Post by KernelKnight on 2010-02-23
Tried that. Same prompt.

---

### Post by dabl on 2010-02-23
Bummer.

You say it started yesterday.  Was there anything done with the system (BIOS upgrade, Windows reinstalled, etc.) that might have changed the boot flag on the mbr?

Also, I'm wondering about the kernel boot line in the grub menu.  Did you run upgrade yesterday?  Did you notice whether it finished with "update-grub"?  It might be worth a try to
```

sudo update-grub
```

If that doesn't work, I think the next advice will be 
```

sudo grub-install /dev/sda
```

---

### Post by KernelKnight on 2010-02-23
I played around with a Backtrack 4 CD, but I didn't install anything.

---

### Post by dabl on 2010-02-23
If you boot a Live CD, can you 
```

sudo mkdir /mnt/SDA

sudo mount -t ext4 /dev/sda1 /mnt/SDA
```

?

It should mount with no errors.  If it does, then that's an indicator that the problem has something to do with Grub or the partition table, I think.

---

### Post by dabl on 2010-02-23
One more thing to check:
```

cat /etc/default/rcS
```

In case it's the old UTC thing.

---

### Post by KernelKnight on 2010-02-23
```
#
# /etc/default/rcS
#
# Default settings fo the scripts in /etc/scS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the initscripts package

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no

```

---

### Post by KernelKnight on 2010-02-23
Do I do this inside the live CD? Or do I do this during the prompt?

sudo mkdir /mnt/SDA

sudo mount -t ext4 /dev/sda1 /mnt/SDA

---

### Post by dabl on 2010-02-23
Do that from a Live CD session.  Post if there are errors, otherwise it should mount.

---

### Post by KernelKnight on 2010-02-23
Seems like it mounted alright.

---

### Post by dabl on 2010-02-23
OK.  So, that, in conjunction with the fsck results, tells us there is nothing wrong with the filesystem or the partition.

Meaning, there is some problem with Grub or the kernel that is to be booted.

Do you have more than one kernel available in the boot menu?

---

### Post by KernelKnight on 2010-02-23
Yes, I have three.

---

### Post by dabl on 2010-02-23
Highlight the next oldest kernel, and try booting that one.

---

### Post by KernelKnight on 2010-02-23
Have tried all three. Nothing works.

---

### Post by itsjustarumour on 2010-02-23
I downloaded the latest Ubuntu updates about 5 hours ago, just rebooted my laptop for the first time, and I have this same problem.

Can't investigate further at the moment as I'm at work, but just wanted to add my voice to this thread.


EDIT - please ignore this post - I think my problem is best described here [http://ubuntuforums.org/showthread.php?t=1412053&highlight=gave+up+waiting+for+root+device](http://ubuntuforums.org/showthread.php?t=1412053&highlight=gave+up+waiting+for+root+device)  so I'll investigate there - don't want to double-post!  :)

---

### Post by dabl on 2010-02-24
All I can come up with at this point is a very unsatisfying "must be some Grub2 issue", and this:

[http://ubuntuforums.org/showthread.php?t=1391446](http://ubuntuforums.org/showthread.php?t=1391446)

If you want to, try Ctrl-D at that shell prompt, and then the down arrow, and see if it proceeds with booting.

In legacy grub, that message typically indicated some issue with the hard drive setup in BIOS, or a partitioning problem, but I don't see anything wrong there (check over your hard drive arrangement in BIOS -- if SATA, try "legacy IDE mode" and "AHCI" mode).  Therefore Grub2 seems to have some issue, and it's not obvious what that issue might be because you're not getting a specific enough error to tell what the problem is.

If you want, from the Live CD you can try a reinstallatio of Grub2, following the guidance here:

[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

There's no difference between Kubuntu and Ubuntu on this topic.

---

### Post by KernelKnight on 2010-03-01
I can't seem to get anything to work. What would I loose if I just reinstall? I have the home folder on a separate partition, so personal data will still be there, but I am worried about loosing my apps? Should I reinstall? What should I consider?

---

