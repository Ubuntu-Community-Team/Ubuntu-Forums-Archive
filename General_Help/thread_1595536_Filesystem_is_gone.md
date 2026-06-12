---
title: "Filesystem is gone"
date: 2010-10-13
forum: General Help
---

### Post by Zilioum on 2010-10-13
Hi,

my harddisk just died on me for the second time and I cant seem to fix the filesystem. 
But first, heres the whole story: A few weeks ago I bought a mushkin 60gb ssd. I put it in the notebook I owned at that time and everything worked perfectly. A week ago I bought a new notebook, put the ssd in and installed the 10.10 beta. The disk utility showed some bad sectors and showed an elevated "Reallocated sector count". The icon was still green so I didn't worry to much although I know I have to replace the disk at some point. I think that I didn't have this sector problem on my old notebook, which also ran 10.10. 
Now the real Problem: I tried to wake my notebook up from the "suspend" state but the screen stayed black and I only saw the little arrow flickering around. I pressed the power button to reboot and I got the message "No boot device found". I'm booting from an usb stick now and GParted shows my whole disk (which used to be /dev/sda1) as unallocated and displays a warning "/dev/sda:unrecognized disk label". 
Running ```
fsck.ext4 /dev/sda 
``` gives me:```
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda

```
Trying to run "e2fsck" with the appropriate backup superblock number gives me: ```

ubuntu@ubuntu:~$ sudo e2fsck -b 32768 /dev/sda
e2fsck 1.41.12 (17-May-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sda
```

First of all I want to restore that partition, so that I can make an image of the disk (I do have a data backup, but I dont feel like reinstalling the whole thing after I get a new ssd).
Second of all, I would like to know what happened.

Your help is really appreciated!

---

### Post by Zilioum on 2010-10-18
I reinstalled everything on the original harddrive the pc came with and will return the ssd.

---

