---
title: "cryptsetup, losetup not working"
date: 2011-03-22
forum: General Help
---

### Post by I-hate-captcha on 2011-03-22
I'm trying to mount an encrypted file but for some reason Ubuntu doesn't like it.  I've tried Ubuntu and Kubuntu 10.10 64 bit versions.

These are the commands that I am using and the replies I get, which incidentally work perfectly on 2 other recent Linux distributions -

```
sudo /sbin/modprobe dm_crypt
sudo /sbin/modprobe serpent
sudo losetup -f
/dev/loop0
sudo losetup /dev/loop0 /media/usb/.mycryptfile
sudo cryptsetup create mycrypt /dev/loop0
Enter passphrase: *************************
mkdir ~/.Swap
sudo mount -t auto /dev/mapper/mycrypt /home/me/.Swap
mount: wrong fs type, bad option, bad superblock on /dev/mapper/mycrypt,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg shows -

```
Mar 22 12:15:29 kubuntu-vm kernel: [ 4010.820534] REISERFS (device dm-0): found reiserfs format "3.6" with standard journal
Mar 22 12:15:29 kubuntu-vm kernel: [ 4010.821216] REISERFS (device dm-0): using ordered data mode
Mar 22 12:15:29 kubuntu-vm kernel: [ 4010.829371] attempt to access beyond end of device
Mar 22 12:15:29 kubuntu-vm kernel: [ 4010.829379] dm-0: rw=0, want=15763558064, limit=15000000
Mar 22 12:15:29 kubuntu-vm kernel: [ 4010.829386] REISERFS warning (device dm-0): sh-459 journal_init: unable to read journal header
Mar 22 12:15:29 kubuntu-vm kernel: [ 4010.838660] REISERFS warning (device dm-0): sh-2022 reiserfs_fill_super: unable to initialize journal space
```


Now I read somewhere on this forum (sorry can't find it again) that 10.10 has a problem with cryptsetup using a file formatted with ReiserFS, so I created a new crypt file using ext3, and it still failed to mount.  I can't remember exactly what it said, but it was along the lines of "bad superblock" etc'.

Is there a different command syntax or method for doing this under Ubuntu and variants?

Please ignore any typos in my code example above, I have it all in a script that I simply copy from machine to machine, so it's fully automated and any typos are simply the result of my typing.

Thanks.

---

### Post by I-hate-captcha on 2011-03-22
As a test, I just created a **new** crypt file on my Kubuntu machine and it works.

It seems that it doesn't like "foreign" files, which is still a problem for me as I like to keep all my personal files (my entire home directory) in an encrypted file which I carry on a USB stick and simply mount on each machine I use.

I'll now try using the new crypt file that I created under Kubuntu on several other Linux variants and see if that works.

---

