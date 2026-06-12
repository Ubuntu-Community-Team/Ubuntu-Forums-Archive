---
title: "[karmic] Partition slow to mount"
date: 2010-01-10
forum: General Help
---

### Post by svanechel on 2010-01-10
Hi,

I'm experiencing something pretty weird with single partition of a physical disk that contains other partitions. I have observed twice already that after a boot that particular partition is not available, i.e. it does not appear to be mounted. When I tried to manually mount that partition, I got the message "not mounted or device busy". Unmounting the device showed that it was actually not mounted, although I cannot fathom what would keep the device busy. It is the only partition on that physical disk that has this problem, which is good because my root partition is also on this disk.

The first time I had this I tried rebooting a couple of times (after, unsuccessfully, trying the manual mount) and it seemed to work. The partition became available again.

This time I was still busy googling for it when suddenly the partition became available, i.e. it had mounted. After a reboot it stayed that way.

As I am unable to comprehend this and quite convinced that it will pop up again in the future, I wonder if someone else has seen this or knows what is going on.

All partitions are formated as ext3 and I'm currently running karmic (clean install), although the offending partition has not been touched since 8.04. My machine is a Dell Studio 17 laptop.

Thanks in advance,

Sven

---

### Post by Morbius1 on 2010-01-10
I'm assuming you are having it auto mount through fstab?

Post the output of the following commands so we can see what's going on:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **mount**
Type **cat /etc/fstab**

And please identify the partition that is giving you grief.

---

### Post by svanechel on 2010-01-22
Sorry it took so long for me to reply with the requested info. I had a lot on my mind lately. I am indeed auto-mounting it with fstab. Here's the output of the commands you requested:

gigabox:~> sudo blkid -c /dev/null
[sudo] password for sven: 
/dev/sda1: UUID="1cd52e64-f16a-4bc3-a44f-f00ecae9c9ad" TYPE="ext3" 
/dev/sda5: UUID="d8c24af2-abf3-4ce5-ad85-db62982054ef" TYPE="swap" 
/dev/sda6: UUID="c8e1912c-370a-4eb7-951b-46f149464027" TYPE="ext3" 
/dev/sda7: UUID="bac9a827-6b5c-4777-90b4-6d581b8b02bf" TYPE="ext3" 
/dev/sdb5: UUID="c292ff53-84cb-416b-9b48-0391e9e374ed" SEC_TYPE="ext2" TYPE="ext3" 
gigabox:~> mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda6 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda7 on /storage/bytestore2 type ext3 (rw)
gvfs-fuse-daemon on /home/sven/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sven)
gigabox:~> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1cd52e64-f16a-4bc3-a44f-f00ecae9c9ad /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=c8e1912c-370a-4eb7-951b-46f149464027 /home           ext3    defaults        0       2
# /storage/bytestore was on /dev/sdb5 during installation
UUID=c292ff53-84cb-416b-9b48-0391e9e374ed /storage/bytestore ext3    defaults        0       2
#/dev/sdb5 /storage/bytestore ext3    defaults        0       2
# /storage/bytestore2 was on /dev/sda7 during installation
UUID=bac9a827-6b5c-4777-90b4-6d581b8b02bf /storage/bytestore2 ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=d8c24af2-abf3-4ce5-ad85-db62982054ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

The partition I'm talking about is /dev/sdb5 (UUID="c292ff53-84cb-416b-9b48-0391e9e374ed"). From blkid I can see now that SEC_TYPE="ext2", while all the others have TYPE="ext3". I don't know how it ended up like that, as it always has been ext3 (see fstab). What is SEC_TYPE anyway?

I hope this provides you with enough info to diagnose the problem.

Thanks so far already,

Sven

---

### Post by Morbius1 on 2010-01-22
The way I remember it, SEC_TYPE is "secondary type". it means that the partition could have been mounted as ext2 instead of ext3. ext3 is ext2 + journaling so all ext3 partitions can be mounted as ext2. If I do a blkid on my system only one partition has a SEC_TYPE and it's the oldest and formatted using a different tool and distro than my current. I don't think that's the source of the problem. 

Having said all that, I'm afraid I can't find anything wrong with your setup. Although based on your output, it's clearly not currently mounted.

I'll keep looking at this - must be some obvious I'm missing.

---

### Post by svanechel on 2010-01-22
If it is any help, I just experienced it again. Since I by now know that it is slow to mount, as opposed to not mounting at all, I patiently waited 5 mins or so and then rebooted. Experience taught me that rebooting immediately doesn't help, however keep on rebooting until a couple of minutes have expired works (I conjecture). All of this is based on a very small sample set (it has happened 3 times so far in the space of a couple of months), so I don't know how consistent this behavior actually is and don't quite know which remedy or workaround works best.

After the reboot, the offending partition was scheduled for a check-up. No problems were found and the system further booted normally, with the partition mounted again as if nothing ever happened.

Sven

---

### Post by Morbius1 on 2010-01-22
I wonder if it's a mechanical problem. Try "reseating " the disk connections. It may be that the connector either to the disk or the motherboard has become dislodged.

---

### Post by svanechel on 2010-01-23
It is a laptop, so that would be highly unpractical :-) I can call in Dell (I still have a repair-at-home-even-on-saturdays contract), but I think I would need to be a little bit more sure it is a hardware problem. What mechanism could cause the slow mounting of a device (no easy answer, I know)? I do not haul my laptop around, so how can a connector become dislodged? Besides, why would it only crop up in Karmic? Here's the thing, months ago I installed Karmic, and then went back to Jaunty because I had some other issue with Compiz (which turned out to be a bug in the ATI driver). Last month I did a clean install of Karmic again. I have only seen the issue come up in Karmic. Although, as I said before, the sample size is to small to know for sure. It can all be down to coincidence.

Thanks for the help so far,

Sven

---

### Post by henriquemaia on 2010-01-23
I'm having the exact same problem as you, with all the symptoms you describe (my output of the above commands is exactly the same as yours, even the sec_type). When I writing this, my drive still hasn't mounted. This happened 3 or 4 times in the past year, but always following this pattern. I too wished that there was a way to solve this. It's not too critical since I have backups of that particular partition/disk, but it's very annoying.

---

### Post by svanechel on 2010-01-24
@henriquemaia: thanks for increasing the sample size :-) Do you have this with Karmic or do you have it or have seen it with previous versions? What's your hardware?

---

### Post by svanechel on 2010-02-08
If anyone is still listening, I think I have some more info. I just happened again and I think I know what triggers it (or at least what event seems to always happen just before it happens. Each time it happens a disk check is run during booting, probably on the offending partition. Since this is a rather large partition, I find it stops way too early. Trying the usual remedy (waiting a while, then rebooting), results in a new disk check, this time without any problems, taking a while to finish.

I can clearly hear my disk, so I conjecture that the disk check is still busy, and that the boot incorrectly concluded it had already ended. This seems to be confirmed by the fact that top revealed that fsck.ext3 is still running.

Although I now am convinced that this is largely harmless, I am convinced that this is a bug. What do you think?

Sven

---

### Post by svanechel on 2010-02-08
I have just filed a bug report (#518928, see [https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/518928](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/518928))

---

### Post by Richard1979 on 2010-02-08
I'm pretty sure this is a known issue under 9.10:
[http://www.ubuntu.com/getubuntu/releasenotes/910#Login%20screen%20presented%20before%20optional%20filesystems%20are%20mounted](http://www.ubuntu.com/getubuntu/releasenotes/910#Login%20screen%20presented%20before%20optional%20filesystems%20are%20mounted)

---

### Post by svanechel on 2010-02-09
@Richard1979: you are right. Strange I did not find it before, as I know I have looked. In any case I've marked my bug report to be a duplicate of #439604

---

### Post by Richard1979 on 2010-02-10
> **svanechel said:**
> @Richard1979: you are right. Strange I did not find it before, as I know I have looked. In any case I've marked my bug report to be a duplicate of #439604

If you need to fix it yourself (because you need to boot)
[http://www.digit4l.net/2010/02/fixing-ubuntus-device-not-ready-boot-problem/](http://www.digit4l.net/2010/02/fixing-ubuntus-device-not-ready-boot-problem/)
Not spam - this is the personal way that I fixed it.

---

