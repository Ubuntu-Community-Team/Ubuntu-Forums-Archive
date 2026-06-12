---
title: "105GB Root Partition?"
date: 2009-09-16
forum: General Help
---

### Post by raywood on 2009-09-16
I'm running 9.04 x64.  My / partition is 107GB.  Somehow, it got full.  I noticed, a while back, that it was reporting 45GB, but Acronis True Image squeezed it down to ~10GB.  It didn't occur to me, then, that the 45GB number would grow; but now it has done exactly that.  This morning, the drive is too full to run some programs.

I've tried this:

```
sudo find / -type f -size +1000000k
```

This, I think, is a search for all files greater than 1GB.  It doesn't seem to turn up any surprises.  Any other suggestions?  (Note:  I have no other Ubuntu partitions aside from / and swap.)

---

### Post by raywood on 2009-09-16
As I check back, I find that even the remaining space I had now appears to be full.  I can no longer open Gparted or Synaptic, for example, from the Ubuntu menu; I get messages like, "Failed to run /usr/sbin/gparted as user root.  Unable to copy the user's Xauthorization file."

---

### Post by sunchiqua on 2009-09-16
Show us the output of:

```
df -h
```

---

### Post by drs305 on 2009-09-16
The three most common causes are unemptied trash bins (including root's), back ups saved on the system partition instead of on a back up partition, and really large log files. When troubleshooting a full system partition it is useful to unmount all non-system partitions. This prevents other mounted folders from 'hiding' potential problems.

I wrote a guide on troubleshooting disk space problems. Here is the link:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by raywood on 2009-09-16
Wow, you folks are pretty fast on the draw this morning.  But yeah, it was root trash.  I doubt I had ever emptied it.  Thanks!

---

### Post by PenquinCoder on 2009-10-10
Hello all,

I'm having the same issue now, after backing up the system using Simple backup.

I had originally been using rsync to do my backups, but yesterday used Simple Backup. I left it on overnight, to backup to an external harddrive. However I come back this morning, and my root partition (of 28g) is completely 100% full!!

I have tried removing root's trash (/root/.local/Trash) but there is NO Trash folder.

My harddrive partitions are encrypted with LUKS, but pulling up a df -h shows this:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/sda3_crypt
                       28G   28G     0 100% /
tmpfs                 2.4G     0  2.4G   0% /lib/init/rw
varrun                2.4G  344K  2.4G   1% /var/run
varlock               2.4G     0  2.4G   0% /var/lock
procbususb            2.4G  176K  2.4G   1% /proc/bus/usb
udev                  2.4G  176K  2.4G   1% /dev
tmpfs                 2.4G  140K  2.4G   1% /dev/shm
lrm                   2.4G  2.5M  2.4G   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda1             190M   35M  146M  20% /boot
/dev/mapper/sda4_crypt
                      116G   60G   51G  54% /home
overflow              1.0M   32K  992K   4% /tmp

/dev/mapper/truecrypt1
                       99G   41G   54G  44% /media/truecrypt1
/dev/sdb1             366G   55G  312G  15% /media/fat32

```

The /dev/mapper/truecrypt1 (actually a second partition on /dev/sdb) is the path I gave to Simple Backup to place files. These files are there, and so the backup did place the files in the correct location.

However, I still cannot get my root partition down to a reasonable size (it was about 14% before I did that backup). I've run apt-get auto clean, apt-get clean, and a Ubuntu 'cleaner' script that clears out the cache's and all trash locations.

I still cannot run programs as root, most notable gdebi under the guise of 'Xauthority' errors. 


Could anyone please assist me in finding the commands or procedure for regaining the space of my root partition??

---

### Post by PenquinCoder on 2009-10-11
I have solved my own error, thank you.

For some reason, even if my external harddrive IS mounted, and browsable, it doesn't show up in the fstab. I believe this is because it is an encrypted partition, and is actually handled by truecrypt mapper, and not fstab? 


At any rate, I fixed the error by unmounting my external drive, and then deleting the folder under /media that pointed to the drive. This cleared my root partition back to the 14% I originally had.

---

