---
title: "howto mount encrypted partition on bootup, which was created by palimpsest?"
date: 2009-11-26
forum: General Help
---

### Post by monkman on 2009-11-26
ubuntu 9.10, 64bit, swap and home encrypted on installation with alternative cd. no problems, runs fine.

now i had an partition, which i didn't configure on installation. with palimpsest i made an ext4 partition with encryption and want to mount this automatically on bootup, by adding this to fstab. so the passphrase is getting asked for before logging into the system, like home and swap.

when i add this partion to fstab and crypttab, like the others i aready have, it doesn't work. i have to enter the passphrase again entering the partition in nautilus

fstab
```
/dev/mapper/sda7_crypt /home           ext4    defaults        0       2
/dev/mapper/sda5_crypt none            swap    sw              0       0
/dev/mapper/sda8_crypt /media/sda8	ext4	defaults	0	2
```

crypttab
```
sda5_crypt /dev/disk/by-uuid/32dd159a-5d83-4296-b854-dd17cca8a410 none luks,swap
sda7_crypt /dev/disk/by-uuid/fe6c5579-b30b-4bb4-80ce-2610b59c1e6a none luks
sda8_crypt /dev/disk/by-uuid/9fe9503e-eefb-451b-94fe-84039df03299 none luks
```

blkid
```
/dev/sda1: UUID="2AE80D4BE80D16AB" LABEL="39GB" TYPE="ntfs" 
/dev/sda5: UUID="32dd159a-5d83-4296-b854-dd17cca8a410" TYPE="crypto_LUKS" 
/dev/sda6: UUID="bd431239-60ef-40be-bfb2-2eb8256c73a8" TYPE="ext4" 
/dev/sda7: UUID="fe6c5579-b30b-4bb4-80ce-2610b59c1e6a" TYPE="crypto_LUKS" 
/dev/sda8: UUID="9fe9503e-eefb-451b-94fe-84039df03299" TYPE="crypto_LUKS" 
/dev/sdb1: LABEL="backup" UUID="aaecd615-6c38-4e2b-9c00-987b6707dba7" TYPE="ext4" 
/dev/mapper/sda5_crypt: UUID="5b27b04c-652a-40f2-98c4-5be80e6c3bb8" TYPE="swap" 
/dev/mapper/sda7_crypt: UUID="46582b59-8265-4da8-990f-54da94110028" TYPE="ext4" 
/dev/mapper/devkit-disks-luks-uuid-9fe9503e-eefb-451b-94fe-84039df03299-uid1000: LABEL="576GB" UUID="3d92ab1e-90cd-4bf1-94e6-c22a18cdd8ac" TYPE="ext4" 
```


i see there is a difference between sda5/sda7 and sda8. is that my problem? how do i avoid this?

thx!

---

### Post by sisco311 on 2009-11-26
```
/dev/mapper/[COLOR="Red"]sda5_crypt[/COLOR]: UUID="5b27b04c-652a-40f2-98c4-5be80e6c3bb8" TYPE="swap" 
/dev/mapper/[COLOR="Red"]sda7_crypt[/COLOR]: UUID="46582b59-8265-4da8-990f-54da94110028" TYPE="ext4" 
/dev/mapper/[COLOR="Red"]devkit-disks-luks-uuid-9fe9503e-eefb-451b-94fe-84039df03299-uid1000[/COLOR]: LABEL="576GB" UUID="3d92ab1e-90cd-4bf1-94e6-c22a18cdd8ac" TYPE="ext4"
```

fstab entry:
```
dev/mapper/[COLOR="Red"]devkit-disks-luks-uuid-9fe9503e-eefb-451b-94fe-84039df03299-uid1000[/COLOR]    /media/sda8	ext4	defaults	0	2
```

---

### Post by monkman on 2009-11-26
i altered my files like shown, and the passphrase is asked for before i log into the system.

but: when i click the sda8 "576GB" drive in nautilus now, it wants the root password for authorization when mounting or unmounting it. even though i chowned it. how do i avoid this? shouldn't it be mounted already when logging in?

thx!

---

### Post by SIODSeraph on 2009-11-26
It could be related to the location where you try to mount this partition to. Maybe you could try creating a folder in /home call it data or whatever, change ownership to the user that you are and edit the entries in fstab to mount to /home/data instead.

Just an idea that I am throwing out. Not sure if that would fix anything but worth a shot.

Cheers,
Sebastian

---

### Post by monkman on 2009-11-26
didn't work.

but i think it would be wise for this partition, to encrypt via trucrypt. it will contain just files, which will outlive at least the next 5 ubuntu releases... i think for this scenario, it's the best way to stick with truecrypt...

---

### Post by rfaull on 2010-01-07
I have a similar problem with Karmic and palimpsest. After creating an encrypted partition with palimpsest, I can mount it and use files until a reboot. After that, the partition is not recognised and has to be reformatted to recover the space on the drive; of course, any data is lost.

If I create an encrypted partition using these instructions ([http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/](http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/)), the partition remains after a reboot but is only mountable with root privileges after user login.

Is there a way -- as implied when the partition is created with palimpsest -- to allow the partition to be mounted by the user at login? I have tried various ways suggested for /etc/crypttab and /etc/fstab, without success. My search of the web has been unhelpful.

---

