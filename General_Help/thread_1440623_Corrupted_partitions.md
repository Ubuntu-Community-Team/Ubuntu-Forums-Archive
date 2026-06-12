---
title: "Corrupted partitions"
date: 2010-03-27
forum: General Help
---

### Post by Dhee on 2010-03-27
About a week ago after an Ubuntu update, I got the following message  upon booting the computer:

```

grub error
reason: unknown filesystem
grub rescue 
```Not wanting to lose my data, I popped in my  Win7 cd, and loaded up that MBR, so I could atleast use my computer.  Previously, I could see the partition from Win7, but now I can't even do  that. Now, even when booting an Live CD, I get the following message  when I'm trying to mount the Ubuntu partition. 

```

Error  mounting: mount exited with exit code 32: mount: wrong fs type, bad  option, bad superblock on /dev/sda5, missing codepage or helper program,  or other error. In some cases useful info is found in syslog - try  dmesg | tail  or so

```Upon following that suggestion

```

ubuntu@ubuntu:~$  dmesg | tail
[  195.856868] zd1211rw 1-7:1.0: phy0
[  195.856900]  usbcore: registered new interface driver zd1211rw
[  365.854968]  SQUASHFS error: squashfs_read_data failed to read block 0x13420ecd
[   365.854978] SQUASHFS error: Unable to read data cache entry [13420ecd]
[   365.854982] SQUASHFS error: Unable to read page, block 13420ecd, size  a28c
[  365.872779] SQUASHFS error: Unable to read data cache entry  [13420ecd]
[  365.872787] SQUASHFS error: Unable to read page, block  13420ecd, size a28c
[  532.340158] EXT4-fs (sda5): Couldn't mount  because of unsupported optional features (4ba62c21)
[  560.586595]  EXT4-fs (sda5): Couldn't mount because of unsupported optional features  (4ba62c21)

```I googled around a bit, but I'm pretty stumped on this one. Is there  anybody who has an idea to either fix this, or a way that I can atleast  recover my data before formatting the whole partition?

---

### Post by Mark Phelps on 2010-03-27
MS windows can NOT read or write Linux partitions.  

You have to install a third-party product like e2fprogs to do that.  

And even then, that can not work with the Ext4 partitions created by default in Ubuntu 9.10.

If you want to rescue stuff off your Ubuntu partition(s), best approach is to boot with a LiveCD and copy the file you want off to USB stick or USB drive.

---

### Post by john newbuntu on 2010-03-28
Use the liveCD and run a filesystem check on /dev/sda5 and see if you find any problems.

```
sudo e2fsck -C0 -p -f -v /dev/sda5
```

---

### Post by Dhee on 2010-03-30
I tried it, and this is what came out:

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
e2fsck: Filesystem revision too high while trying to open /dev/sda5
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)

/dev/sda5: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device> 
```

Then, upon doing

```
e2fsck -b 8193 /dev/sda5
```

```

ubuntu@ubuntu:~$ sudo e2fsck -b 8193 /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Bad magic number in super-block while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

---

### Post by kelt65 on 2010-03-30
Well, evidently, the version of e2fsck on the CD does not support ext4.

Can you mount it with no options passed? What options do you have in /etc/fstab?

---

### Post by NiGhtMarEs0nWax on 2010-03-30
here is some useful info, you need to be root.

[COLOR="Blue"]_[link1]("http://www.linfo.org/superblock.html")_ _[link2]("http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/")_[/COLOR]

---

### Post by Dhee on 2010-04-01
> **kelt65 said:**
> Well, evidently, the version of e2fsck on the CD does not support ext4.

Can you mount it with no options passed? What options do you have in /etc/fstab?

I'm not able to mount it.

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0
```Alright, I've never seen this kind of report before, or is this because I'm working from a Live CD here?

> **NiGhtMarEs0nWax said:**
> here is some useful info, you need to be root.

[COLOR=Blue]_[link1]("http://www.linfo.org/superblock.html")_ _[link2]("http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/")_[/COLOR]

Will try that, thank you.

Edit; That is a negative...

---

### Post by john newbuntu on 2010-04-01
The answers to your problem can be found by the user "jerryUs" towards the end of this post:
[http://ubuntuforums.org/archive/index.php/t-807055.html](http://ubuntuforums.org/archive/index.php/t-807055.html)

---

### Post by Dhee on 2010-04-04
> **john newbuntu said:**
> The answers to your problem can be found by the user "jerryUs" towards the end of this post:
[http://ubuntuforums.org/archive/index.php/t-807055.html](http://ubuntuforums.org/archive/index.php/t-807055.html)

I thank you sir, it solved my problem.

---

