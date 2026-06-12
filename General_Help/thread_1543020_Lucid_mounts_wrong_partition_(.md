---
title: "Lucid mounts wrong partition :("
date: 2010-07-31
forum: General Help
---

### Post by fopetesl on 2010-07-31
I have two identical SATA 640GB drives.
I wish to mirror copy regularly for backup.

My CDROM is also SATA but my ASUS M2V motherboard only has two SATA connections.

I did my first mirror OK using dd if=/dev/sda of=/dev/sdb bs=8225280

Then I switch off and disconnect one drive leaving it as sda and plug in the CDROM to 2nd SATA port to continue working.

Now, however, Lucid mounts the wrong partition as /

With one drive```
~$ mount
[COLOR="DarkGreen"]/dev/sda8 on / type ext4 (rw,errors=remount-ro)[/COLOR]
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sda9 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/almeter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=almeter)
```
.. with two drives..```
~$ mount
[COLOR="Red"]/dev/sdb8 on / type ext4 (rw,errors=remount-ro)[/COLOR]
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sda9 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/almeter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=almeter)
```I obviously cannot umount /dev/sdb8 and performing a dd copy will copy the wrong partition(s).

How do I get around this?

BTW, I allowed an upgrade which gave me kernel 2.6.32-22-generic #32-Ubuntu SMP hoping it would solve my problem but it won't boot.  Locks up part way through.
So I'm using 2.6.32-21-generic since it seems to work without a hitch. Maybe.

---

### Post by WorMzy on 2010-07-31
Edit fstab and replace /dev/*** with UUID=**********. You can find out what your partition's UUIDs are by running ```
blkid -c /dev/null
```
You can edit fstab with
```
gksu gedit /etc/fstab
```

If you're unsure on what to do, post the contents of fstab, and the output of blkid here, surrounding both with [CODE[COLOR="Black"]][/COLOR][/CODE] tags.

EDIT: I don't think that dd copies the UUID, but maybe it does, and that's what's going wrong. You can generate a new UUID for a partition by running 

```
sudo tune2fs -U random /dev/***
``` (replacing *** with the partition you need a new UUID on)

---

### Post by prodigy_ on 2010-07-31
What's in your **/boot/grub/grub.cfg**? Also what does ```
sudo blkid
``` say?

I imagine that when you **dd** a partition, its UUID gets copied as well.

---

### Post by fopetesl on 2010-08-02
> **WorMzy said:**
> Edit fstab and replace /dev/*** with UUID=**********. You can find out what your partition's UUIDs are by running ```
blkid -c /dev/null
```
Nice answer, Wormzy but I can see a potential pitfall.

Follow your instructions and I will have different UIDs. OK.
So the mirror copy should now work as desired.

One day, hopefully in the far future, /dev/sda dies. :(
No worries. I have a backup :)
Oops! /etc/fstab has the wrong UID(s) for booting.

So I guess the only final answer is to boot a live CD/DVD and edit /etc/fstab again?

---

### Post by WorMzy on 2010-08-02
I'm afraid so; but pretty much every backup method has some level of inconvenience, booting into a live CD and altering a line in fstab (and probably menu.lst/grub.cfg in /boot/grub) is fairly minimal.

---

### Post by fopetesl on 2010-08-02
> **WorMzy said:**
> I'm afraid so; but pretty much every backup method has some level of inconvenience, booting into a live CD and altering a line in fstab (and probably menu.lst/grub.cfg in /boot/grub) is fairly minimal.
Another problem!
Trying to change the BLKID of /dev/sdb6:```
~# sudo tune2fs -U random /dev/sdb6
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb6
Couldn't find valid filesystem superblock.
```because /swap doesn't have a filesystem? But it does have a BLKID```
# blkid -c /dev/null
/dev/sda1: LABEL="98SEC-COPY" UUID="436A-17DD" TYPE="vfat" 
/dev/sda2: LABEL="WIN-XP-SATA" UUID="5AA4F37CA4F35949" TYPE="ntfs" 
/dev/sda5: LABEL="98SED-COPY" UUID="EE64B21B64B1E68D" TYPE="ntfs" 
/dev/sda6: UUID="ea361d26-3a63-48b7-8130-53e2fa3c10b1" TYPE="swap" 
/dev/sda7: LABEL="Conversions" UUID="AD09F37325B29AD3" TYPE="ntfs" 
/dev/sda8: UUID="726e0e62-d7ec-44d6-8a98-12a50c76c30d" TYPE="ext4" 
/dev/sda9: UUID="82d5a9b4-e186-427a-ad99-9475e1d2fec6" TYPE="ext4" 
/dev/sdb1: LABEL="98SEC-COPY" UUID="436A-17DD" TYPE="vfat" 
/dev/sdb2: LABEL="WIN-XP-SATA" UUID="5AA4F37CA4F35949" TYPE="ntfs" 
/dev/sdb5: LABEL="98SED-COPY" UUID="EE64B21B64B1E68D" TYPE="ntfs" 
/dev/sdb6: UUID="ea361d26-3a63-48b7-8130-53e2fa3c10b1" TYPE="swap" 
/dev/sdb7: LABEL="Conversions" UUID="AD09F37325B29AD3" TYPE="ntfs" 
/dev/sdb8: UUID="726e0e62-d7ec-44d6-8a98-12a50c76c30d" TYPE="ext4" 
/dev/sdb9: UUID="82d5a9b4-e186-427a-ad99-9475e1d2fec6" TYPE="ext4"
```How to change?

Could be used at boot same as /dev/sdb8?

---

### Post by WorMzy on 2010-08-02
I think that UUIDs was a bad idea, I didn't realise that dd duplicated them too.

I think the best thing to do would be to open fstab and switch all UUIDs to /dev/sd**; and if, when you plug the backup drive in, it boots to the wrong drive, reboot into the bios options and reorder the disks there.

You may need to modify your grub entries too, since I think Ubuntu grub entries use UUIDs to set the root at boot time. Not sure how you'd do that in grub 2 (which is what Lucid used by default, assuming you didn't upgrade from Jaunty or an older version of Ubuntu).

What you're doing is basically making an asynchronous RAID 1, and I'm sure that plenty of other people have managed to set up a RAID 1 without any problems, so there must be some way to get it to work. So don't give up. :)

---

### Post by fopetesl on 2010-08-03
> **WorMzy said:**
> 
What you're doing is basically making an asynchronous RAID 1, and I'm sure that plenty of other people have managed to set up a RAID 1 without any problems, so there must be some way to get it to work. So don't give up. :)Not giving up, Wormzy.  Can't afford the risk.
However, RAID 1 I'm not keen on mostly because BOTH drives are running ALL the time.  Even though WD WD6400AAKS MTBF is quoted as 750K hours there still HAS to be a risk of HD failure :(  I'd much rather backup and swap drives regularly.

So I'll try the fstab/grub (some reading to do here) route...

---

