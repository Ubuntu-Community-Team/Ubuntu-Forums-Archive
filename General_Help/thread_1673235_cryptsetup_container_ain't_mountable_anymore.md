---
title: "cryptsetup container ain't mountable anymore"
date: 2011-01-22
forum: General Help
---

### Post by hifishi on 2011-01-22
Hi,

i have a cryptsetup container, which after freshly setting up the computer isn't mountable anymore. Google didnt help me much so i hope i can find help here.

Since i use a keyfile, it cant be the passphrase.

This is what i do:
> losetup /dev/loop0 /home/data.img
cryptsetup -d super-secret-key.file data /dev/loop0
mount /dev/mapper/data /data
->mount: you must specify the filesystem typeI can't remember the filesystem of the container exactly but it should be ext4/3 or xfs.
Tried them all (and more) with the mount option no success.

I am kinda lost now what can i do  / check / try to rescue the data? :confused:

Any help is really appreciated!

---

### Post by hifishi on 2011-01-31
noone? :(

---

### Post by I-hate-captcha on 2011-03-22
I'm having the same problem, I think it's something to do with different default values in the newer versions of losetup and cryptsetup.

losetup -N seemed to work, but then there are so many other variables like cipher type, keybits etc'.

I also found I had to modprobe aes in order to get aes128, but it still seems to be using another method all together, and the man pages are useless.

Mount it with - ```
sudo mount -t ext3
```, and tail dmesg, you should see error messages about journals and headers.

---

### Post by a1an on 2011-08-22
I have the same problem after upgrading from Ubuntu 10.04 to 11.04, my cryptsetup container is not mountable while on 10.04 on another pc it still works like a charm.

Any help on how to set it to work as of 10.04 will be greatly appreciated so I can continue using the crypted data with 11.04

regards

---

### Post by a1an on 2011-08-22
Finally I found the cause of the issue and the solution in the release notes of maverick:  [https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

> 
Cryptsetup is not by default compatible with the version in 10.04LTS. An encrypted disk set up under 10.04LTS will fail to properly mount under maverick. This is because, as documented in the /usr/share/doc/cryptsetup/NEWS.Debian.gz, defaults have changed. So to mount a disk which was created in 10.04LTS with cryptsetup, in 10.10 you must specify the cipher as such: cryptsetup -c aes-cbc-plain create h /dev/sdb1 (622762) 


As it can be seen changing defaults is always a source of problems when they are relied upon

---

