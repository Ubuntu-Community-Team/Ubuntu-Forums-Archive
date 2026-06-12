---
title: "No space left on device"
date: 2011-01-19
forum: General Help
---

### Post by Alex1200GS on 2011-01-19
There's a weird thing going on with my Ubuntu server and I'd really appreciate any hints on how to troubleshoot this.

While logged in as root, I can't create any files or move existing ones and I'm confronted with a "No space on device" error. Strange as it may sound, this does not happen while I'm logged in as a normal user (huh???).

```
**df -h**
Filesystem            Size  Used Avail Use% Mounted on
varrun                2,0G  188K  2,0G   1% /var/run
varlock               2,0G     0  2,0G   0% /var/lock
udev                  2,0G   72K  2,0G   1% /dev
devshm                2,0G     0  2,0G   0% /dev/shm
/dev/cciss/c0d0p2      48G   20G   26G  44% /home
/dev/cciss/c0d1p2     276G  138G  124G  53% /mnt/data
/dev/cciss/c0d1p1      19G  3,1G   15G  18% /var
overflow              1,0M     0  1,0M   0% /tmp
```

```
**df -i**
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
varrun                218801      55  218746    1% /var/run
varlock               218801       2  218799    1% /var/lock
udev                  218801    2944  215857    2% /dev
devshm                218801       1  218800    1% /dev/shm
/dev/cciss/c0d0p2    6356992   38632 6318360    1% /home
/dev/cciss/c0d1p2    36634624  213458 36421166    1% /mnt/data
/dev/cciss/c0d1p1    2443200   31987 2411213    2% /var
overflow              218801      11  218790    1% /tmp
```

I have searched all over the internet for this but all hints I get are either focused on actually filled-up partitions or lack of inodes, neither of which applies here.

Here's a little something that may shed some light but I'm not really sure it's related anyway: I recently set up a D-Link NAS in the same subnet, mounted it to the server using sshfs and rsync'ed my data there. It worked smoothly in the first couple of runs but last time I tried rsync-ing I started getting this weird "no space left on device" message. I tried **fusermount -u /mnt/dlink**, got the same annoying message and while **df -h** reported that the dlink drive was still mounted, a second **fusermount -u /mnt/dlink** attempt reported that there's no such fs mounted.

Rebooting the server resolved this but the freaking message remains. And it only annoys the root user.

What on earth could be causing this?
Any hints would be truly appreciated, thanks.

---

### Post by gmargo on 2011-01-19
What device is getting the error?

Is it a problem with running out of space on /tmp?  You only have 1M available which is very small.

> 
While logged in as root, I can't create any files or move existing ones  and I'm confronted with a "No space on device" error. Strange as it may  sound, this does not happen while I'm logged in as a normal user  (huh???).
Root's home directory is /root (on the / partition), while a normal user's is /home/xxxx (on the /home partition).

I don't see any device mounted as / (where the /root would be).

---

### Post by Alex1200GS on 2011-01-19
Thanks gmargo,

I just returned here to report that it also affects normal users:

```
**mail**
mail: /tmp: No space left on device
```

when I saw your reply. You're correct, there's no / mountpoint and as far as I recall, / should be mounted on /dev/cciss/c0d0p1.

Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/cciss/c0d0p1
UUID=5c058ffc-3394-4c4d-b181-f38c7e560c66 /               ext3    defaults,errors=remount-ro 0       1
# /dev/cciss/c0d0p2
UUID=6898e09e-3885-4b2f-a96b-9f7e8bd73d79 /home           ext3    defaults        0       2
# /dev/cciss/c0d1p2
UUID=e9456135-99ac-4d5d-9b16-0e4a0954f0a8 /mnt/data       ext3    defaults        0       2
# /dev/cciss/c0d1p1
UUID=9fa608f3-2364-4cee-8af3-5a95575aa5a3 /var            ext3    defaults        0       2
# /dev/cciss/c0d0p3
UUID=c41e53ef-6089-4cc8-9072-137b377f96af none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

and my mtab:

```
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/cciss/c0d0p2 /home ext3 rw 0 0
/dev/cciss/c0d1p2 /mnt/data ext3 rw 0 0
/dev/cciss/c0d1p1 /var ext3 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
overflow /tmp tmpfs rw,size=1048576,mode=1777 0 0
```

Do you think it is safe to edit these and reboot the server (umount -a displays the error message so that's not an option) or will it blow up the entire thing?

---

### Post by Alex1200GS on 2011-01-19
Oh, great. I tried editing /etc/fstab and while changes were reported to be saved, the file is now empty and I can't restore its contents. What on earth???

---

### Post by Alex1200GS on 2011-01-19
```
**mount -o rw,defaults,noatime -t ext3 /dev/cciss/c0d0p1 /**
mount: /dev/cciss/c0d0p1 already mounted or / busy
```

---

### Post by Alex1200GS on 2011-01-21
After endless hours of searching, reading and experimenting, I managed to troubleshoot and fix the problem.

Clearly, / couldn't get mounted for some reason and that's exactly where the problem was. I had a cron job in place that would retrieve a backup of several GB's from another server every week, but no check for available space on the partition. No wonder / got filled up.

I removed old log files, checked for bad blocks, cleaned the cache, removed some of the oldest backups, and then I was again able to write into my fstab and have its entries restored. As soon as I did, I also managed to mount / manually. Then I rebooted the beast to make sure it went back to normal, and everything worked like a charm again.

Phew!!!

---

