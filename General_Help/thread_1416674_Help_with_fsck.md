---
title: "Help with fsck"
date: 2010-02-26
forum: General Help
---

### Post by kevindubrow on 2010-02-26
Hi, I could use some help running fsck.

My SDA1 appears to be having issues. I cant get my netbook to load. 

I popped in a USB drive with Ubuntu on it so I could try to run fsck on it, but I ran into an issue.

According to Ubuntu, this drive is using the "ext3/ext4" file system. I read an online guide for using fsck and it mentioned that I must designate what file system I am running or it will default to ext2 and corrupt my files. So what command should I run so that fsck knows that I have the ext3/ext4 file system?

Also, could someone check to see if the commands I am running are correct (these are starting from the terminal from the USB drive)?

# init 1

# umount /dev/sda1

# fsck.ext3 /dev/sda1 

The third command is where I am confused as to what I should type. Thanks again!

---

### Post by jocko on 2010-02-26
> **kevindubrow said:**
> Hi, I could use some help running fsck.

My SDA1 appears to be having issues. I cant get my netbook to load. 

I popped in a USB drive with Ubuntu on it so I could try to run fsck on it, but I ran into an issue.

According to Ubuntu, this drive is using the "ext3/ext4" file system. I read an online guide for using fsck and it mentioned that I must designate what file system I am running or it will default to ext2 and corrupt my files. So what command should I run so that fsck knows that I have the ext3/ext4 file system?

Also, could someone check to see if the commands I am running are correct (these are starting from the terminal from the USB drive)?

# init 1

# umount /dev/sda1

# fsck.ext3 /dev/sda1 

The third command is where I am confused as to what I should type. Thanks again!
The command "fsck" is just a wrapper that detects which file system it really is and runs the correct program for that filesystem. For ext2/3 and 4 the proper program is e2fsck.
These commands should do it:
```
sudo umount /dev/sda1
sudo e2fsck -fpv /dev/sda1
```

There's no need to drop to a root shell (which is what "init 1" does), and if you do it from a live cd the file system will not be mounted unless you mounted it yourself, so the umount command will just tell you that /dev/sda1 is not mounted.
The -fpv switch will force (f) the fsck even if the filesystem is marked as clean, automatically repair (p) the filesystem and tell you what it did (v).

---

### Post by sisco311 on 2010-02-26
Optionally, you can add -C0 to the options to get a progress bar:
```
 sudo e2fsck -C0 -fpv /dev/sda1
```

But, you don't have to use the CLI. Just open GParted (System -> Administration), unmount the partition & check it for errors.

---

### Post by kevindubrow on 2010-02-26
Awesome! Thank you very much for the reply. Once I get home I'm going to try this out and let you know how it works.

---

### Post by kevindubrow on 2010-02-28
Hey, no luck there. If you wouldn't mind, could you look at the code that the computer is giving me and tell me what you think my next step should be?

I attached a picture. The loading logo pops up, hangs for a long time, and then this pops up.

Thanks!

---

