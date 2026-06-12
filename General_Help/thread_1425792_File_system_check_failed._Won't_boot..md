---
title: "File system check failed. Won't boot."
date: 2010-03-09
forum: General Help
---

### Post by turgidtoupee on 2010-03-09
Please help. I've been stupid, and used kleansweep, which deleted a load of files and in the process killed everything. When I boot I get "file system check failed". Then it gives me a command prompt. I really don't want to have to reinstall ubuntu as I have a lot of stuff installed on it. Thanks

EDIT:Using ext3 filesystem, if it helps.

---

### Post by turgidtoupee on 2010-03-09
I have a knoppix and an ubuntu livecd to hand. Please help

---

### Post by MelDJ on 2010-03-09
try
```
fsck
```

---

### Post by turgidtoupee on 2010-03-09
Tried that. Just gave me some stats on the disk and nothing happened. Still wouldn't boot.

---

### Post by turgidtoupee on 2010-03-09
bump. Please help

---

### Post by Method X on 2010-03-09
> **turgidtoupee said:**
> bump. Please help

Bad problem.
A friend of mine faced it. He started disk checking without unmouting it. Everything was lost.

**Not an advise**, but i'd prefer to reinstall. :(
Sry

---

### Post by turgidtoupee on 2010-03-09
Daww. What if I do it from livecd, while not mounted?

---

### Post by Method X on 2010-03-09
> **turgidtoupee said:**
> Daww. What if I do it from livecd, while not mounted?

To tell the truth, i don't know.
If i were you, i'd tried to boot from live cd, save everything that you can save and reinstall the system, but maybe somebody knows another way? :confused:

but wait, i've found smth...


Here, try this one.

Bootup from Live CD, than go to terminal and:

sudo blkid

it will return something like:

/dev/sda5: UUID="eae4ddca-b9b1-48d4-abba-e26bc44027a4" TYPE="ext4" 
/dev/sda6: UUID="7ff08df9-693a-4841-a459-b934c672a821" TYPE="swap" 

(This is mine result, sda5 is my ubuntu partition).

Ok

copy its UUID

Than open on your filesystem file /etc/fstab

Search for your sda and paste UUID there. (replace wrong UUID number)

---

### Post by turgidtoupee on 2010-03-09
The UUID's were correct. Tried an fsck, it said it was clean. Seems like it's looking more and more hopeless.

---

### Post by Method X on 2010-03-09
> **turgidtoupee said:**
> The UUID's were correct. Tried an fsck, it said it was clean. Seems like it's looking more and more hopeless.

ok, than could you please post here output of:

cat /etc/fstab

---

### Post by turgidtoupee on 2010-03-09
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

Also, I pressed ctrl+D at the error message and it said /etc/default/rcS is missing. I wish I'd knoown this before. I found someone else's but not sure if it'll work.

There's one I get from booting into liveCD too. Would one of these work?

---

### Post by Method X on 2010-03-09
> **turgidtoupee said:**
> aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0


What?
Is it all?
you only see your swap file, but no your filesystem here.
You need bootup to recovery terminal, try it from ubuntu install cd, from boot menu. Login into recovery.
Or from grub recovery. Anyway bootup into your system via terminal and check your fstab. Repeat my advise from previous page. I'm shure it will help.

As i can guess your filesystem is /dev/sda5

Forget now about rcS

---

### Post by turgidtoupee on 2010-03-09
Sorry, that was from the livecd.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=faf7da80-5568-4650-82f0-dc60d1bd1cd8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=db683d86-edda-455f-8d1a-04ad3f3c0fdb none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Method X on 2010-03-09
> **turgidtoupee said:**
> Sorry, that was from the livecd.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=faf7da80-5568-4650-82f0-dc60d1bd1cd8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=db683d86-edda-455f-8d1a-04ad3f3c0fdb none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Ok.
UUID=faf7da80-5568-4650-82f0-dc60d1bd1cd8 / ext4 errors=remount-ro 0 1

look at this line
Change it to
UUID=faf7da80-5568-4650-82f0-dc60d1bd1cd8 / ext4 relatime,errors=remount-ro 0 1


And recheck your UUID

---

### Post by turgidtoupee on 2010-03-09
Done that, still failed with the same /etc/default/rcS missing error.

---

### Post by Method X on 2010-03-09
> **turgidtoupee said:**
> Done that, still failed with the same /etc/default/rcS missing error.

ok.
Almost.
Now look at this short topic: [http://ubuntuforums.org/showthread.php?t=506472]("http://ubuntuforums.org/showthread.php?t=506472")

---

### Post by turgidtoupee on 2010-03-09
Pretty much the same thing, though I was stupid and didn't back up the files. I'll cross my fingers.

---

### Post by Method X on 2010-03-09
> **turgidtoupee said:**
> Pretty much the same thing, though I was stupid and didn't back up the files. I'll cross my fingers.

Thats really bad, but it's a good lesson to make backup.

Anyway, now you can rescue your files, and reinstall system.
Have a rest for some days.

---

### Post by turgidtoupee on 2010-03-09
Copied over /etc/default/rcS. Now I get a different error, "mount of root filesystem failed".

I noticed in the few seconds before reboot that it said something about /dev/shm. This folder is empty.

---

### Post by Method X on 2010-03-09
hmmm....did you tried too bootup into your another available kernel?

---

### Post by pastalavista on 2010-03-09
Boot the live CD and open a terminal. Use fsck like this:```
sudo fsck /dev/sda5
```I just hope you haven't already done too much damage.

---

### Post by turgidtoupee on 2010-03-09
> **pastalavista said:**
> Boot the live CD and open a terminal. Use fsck like this:```
sudo fsck /dev/sda5
```I just hope you haven't already done too much damage.

Done that already, says it's clean.
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda5: clean, 284609/1261568 files, 2033525/5042394 blocks


Tried other kernel, same problem.

---

### Post by Method X on 2010-03-09
> **turgidtoupee said:**
> Done that already, says it's clean.
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda5: clean, 284609/1261568 files, 2033525/5042394 blocks


Tried other kernel, same problem.

Damm, i'm out of ideas, i think its better to reinstall your system. :frown:

---

### Post by turgidtoupee on 2010-03-09
crap. Thanks for helping anyway. So begins he long process of finding everything I want.

---

### Post by pastalavista on 2010-03-09
When you reinstall, use the exact same user name and password. At the partitioner screen, select MANUAL setup and UNCHECK the 'format' boxes from the previous install. This will replace the OS without removing anything created by you. It will overwrite system files so you'll need to do updates again but no files will be lost unless you've lost them already. Good-luck!

---

### Post by turgidtoupee on 2010-03-09
Oh no, I already did it. That would have saved me a lot of hassle.

---

