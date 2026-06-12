---
title: "Unable to access Sdcard reader"
date: 2011-07-15
forum: General Help
---

### Post by sinhapra on 2011-07-15
Hi,
I am new to linux world and have virtual Ubuntu on windows 7. I have connected a sdcard reader to my system but not able to detect sdcard reader. How do I mount my sdcard reader? I used mount command to detect how many device, but I am unable to understand information I recieved

pks@pks-linux-Virtual-Machine:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pks/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pks)
/dev/sr0 on /media/VPCINTGCOMP14.0.7600.16392 type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


Any help in this regard...

---

### Post by dandnsmith on 2011-07-15
Not much help, yet, just some questions:
- how is the reader connected (USB, motherboard connection ...)?
- have you tried inserting an SD card (and then running *mount*)?
- try *sudo fdisk -l* with card inserted
- have a look at the *lshw* output: there will be a lot, and I've no idea what to suggest you look for without some connection information.

---

### Post by sinhapra on 2011-07-15
> **dandnsmith said:**
> Not much help, yet, just some questions:
- how is the reader connected (USB, motherboard connection ...)?
- have you tried inserting an SD card (and then running *mount*)?
- try *sudo fdisk -l* with card inserted
- have a look at the *lshw* output: there will be a lot, and I've no idea what to suggest you look for without some connection information.

Thanks for response..

- how is the reader connected (USB, motherboard connection ...)?
The reader is connected via USB with SD card inserted.
- have you tried inserting an SD card (and then running *mount*)?
Yes, The result I have posted is after inserting sdcard in reader.
- try *sudo fdisk -l* with card inserted
I tried this command, but it returns nothing. 
- have a look at the *lshw* output: there will be a lot, and I've no idea what to suggest you look for without 

Windows 7 shows as V_boot(E:) but ubuntu doesn't show any external device conneted, is it because of I am running ubuntu virtualy?

---

### Post by sinhapra on 2011-07-15
> **sinhapra said:**
> Thanks for response..

- how is the reader connected (USB, motherboard connection ...)?
The reader is connected via USB with SD card inserted.
- have you tried inserting an SD card (and then running *mount*)?
Yes, The result I have posted is after inserting sdcard in reader.
- try *sudo fdisk -l* with card inserted
I tried this command, but it returns nothing. 
- have a look at the *lshw* output: there will be a lot, and I've no idea what to suggest you look for without 

Windows 7 shows as V_boot(E:) but ubuntu doesn't show any external device conneted, is it because of I am running ubuntu virtualy?

I tried lshw and it showing me:
scd0 and sr0 *** extrenal port..I guess it is my usb port, but how do I know which usb port have my sdcard reader?

---

### Post by dandnsmith on 2011-07-16
Wow - talk about unexpected disclosures!
It all depends what you did when creating the virtuality.
Unfortunately I don't have a setup which I could check this out, as I threw my last one away (since it wasn't giving me anything useful).

Perhaps someone else could pick this up - or you could try the appropriate forums for the virtual system you're utilisation (I know there are some for VirtualBox)

HTH

---

