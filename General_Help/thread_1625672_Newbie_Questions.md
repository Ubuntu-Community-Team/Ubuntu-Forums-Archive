---
title: "Newbie Questions"
date: 2010-11-19
forum: General Help
---

### Post by hwuu on 2010-11-19
Hi everyone.
I am totally new at this, so...

Dual booting 10.10 and windows XP. 

1.Where do I find my windows files when I am booted up in Ubuntu? 

2. Where do I find and manage USB devices. My second monitor doesn't turn on in Ubuntu. It uses a USB attached device to connect.

There are probably some other things I should ask but am too new to know it. 

Thanks for any input.

---

### Post by decoherence on 2010-11-19
Ideally, your Windows partition should show up when you go to your "Computer" (under the places menu.)

For USB connected video devices, you probably need the DisplayLink driver. Here's the site [http://libdlo.freedesktop.org/wiki/](http://libdlo.freedesktop.org/wiki/)

Haven't tried this myself, no idea how well it works. Good luck!

---

### Post by ppv on 2010-11-19
The windows partitions could be seen in the file browser. You could use the Computer or Documents link that would open up the browser. In it on the left hand side you would see the various disk partitions. The windows recognised items would have the same Labels as they were in windows. You could simply left click on them and they would auto mount.

---

### Post by sikander3786 on 2010-11-19
> Where do I find my windows files when I am booted up in Ubuntu? 

You can find those as other members mentioned above but ideally it is not recommended to access your Windows partition from any other OS because of many reasons.

1. Important files are not protected when you mount your Windows partition under Ubuntu as they used to be hidden and protected under Windows.

2. Most of the cases, Windows doesn't like many changes to its partition without it being noticed.

3. NTFS-3G driver for Linux is stable but not ideal and might do something wrong. (Many reports on that)

4. You are free to do anything silly...

The real question is why you need your Windows files in Ubuntu? You can ideally set up a separate NTFS /Data partition and use it to share files between Windows and Ubuntu.

---

### Post by Swagman on 2010-11-19
I have **NEVER** had any issues with my NTFS drives in windows after Linux has accessed them.

---

### Post by sikander3786 on 2010-11-19
> **Swagman said:**
> I have **NEVER** had any issues with my NTFS drives in windows after Linux has accessed them.
But that doesn't assure either that you'll never get them :-)

They happen randomly. I had some issues way back with Hardy and Windows XP. Might be I deleted some important Windows files myself... Or the Linux NTFS driver caused problems...

Just to be safe, it is recommended that you create a separate NTFS partition and share files from it.

No problem if you like to survive dangerously :-)

---

### Post by dino99 on 2010-11-19
oh yeah, Hardy is far way back :) now its automatic with maverick

---

### Post by Swagman on 2010-11-19
Well different people have differing experiences but I will say that I started on Ubuntu on 7:04 (Feisty) and before that Debian 64 Dual booting with XP and apart from the *Drive still in use Flag set due to Windows suffering a "Dirty Shutdown" **I have never had a drive issue.

*Cure = reboot into windows and clean shutdown = Problem solved.

** Except when I plugged a molex connector into a hard drive the wrong way  and made the Blue Smoke genie appear ( I never forced it.. honest !!)

---

### Post by hwuu on 2010-11-19
You guys are shooting a little bit above my head, but I think I can follow.

If I keep all the data in one accessible location it will be safer?  I am looking to access xcel spreadsheets emails, word doc's etc.

---

### Post by slooksterpsv on 2010-11-19
> **hwuu said:**
> You guys are shooting a little bit above my head, but I think I can follow.

If I keep all the data in one accessible location it will be safer?  I am looking to access xcel spreadsheets emails, word doc's etc.

Yup that's what they're saying. Essentially, the results will vary from person to person, I haven't had trouble with NTFS volumes, accessing, reading writing data to them, in Linux, but that's not to say I won't either. I couldn't do a Data partition myself for a couple reasons:
1. File Sizes and Fat32 do not mix. 4GB is the maximum file size.
2. Ext# does not really work on windows without additional drivers, even then it still didn't work. 

Otherwise if you need to read and write to small files, like spreadsheets, word processing, etc. I'd use Dropbox that way if one OS fails and you need the files, it's on the online storage.

If you're just listening to music and watching videos, but they're on the NTFS, where that's a read operation, it shouldn't affect the file in any way.

---

### Post by sikander3786 on 2010-11-19
> Yup that's what they're saying. Essentially, the results will vary from person to person, I haven't had trouble with NTFS volumes,

Nobody advised not to use NTFS in Linux. What we were saying is that don't mount your Windows partition in Linux whether FAT32 or NTFS ;-)

One doesn't need to format the shared partition to FAT32. It can be NTFS. In fact I myself use an NTFS partition to share my files between Windows 7 and Ubuntu.

So this is un-related.

> 1. File Sizes and Fat32 do not mix. 4GB is the maximum file size.
2. Ext# does not really work on windows without additional drivers, even then it still didn't work.


You need to create an additional NTFS partition to store your data besides the Windows install partition and use it both in Ubuntu and Windows.

Hope it makes sense this time :)

---

### Post by hwuu on 2010-11-22
> What we were saying is that don't mount your Windows partition in Linux whether FAT32 or NTFS :wink:

I can even figure out where the C: drive is. I don't want to mess up the windows side, but at this point I can't even find it.

Long term I think a shared data partition sounds like a good idea, I think I will work on sorting that out.

---

### Post by sikander3786 on 2010-11-23
> I can even figure out where the C: drive is. I don't want to mess up the windows side, but at this point I can't even find it.

Please post the output of following command to let us figure that out for you :-)

```
sudo fdisk -l
```

And yes, a shared NTFS partition is definitely a long term solution.

---

### Post by hwuu on 2010-11-23
sudo fdisk -l gives the following response:


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc0dbc0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
jeff@ubuntu:~$ ^C
jeff@ubuntu:~$

---

### Post by sikander3786 on 2010-11-23
There is only one partition on your HDD and that should be C:, its NTFS as you see.

> 
/dev/sda1 * 1 9728 78140128+ 7 HPFS/NTFS

Where do you plan to install Ubuntu? By shrinking C: and freeing up some space?

---

### Post by hwuu on 2010-11-23
> **sikander3786 said:**
> Where do you plan to install Ubuntu? By shrinking C: and freeing up some space?


I have been running this dual boot for about a week. Ubuntu is already installed. I had to use ubuntu to run the sudo thing.

After I get things going I am sure I can free up some space from C: it has eight years of business mulch clogging it up.

---

### Post by sikander3786 on 2010-11-23
> **hwuu said:**
> I have been running this dual boot for about a week. Ubuntu is already installed. I had to use ubuntu to run the sudo thing.

After I get things going I am sure I can free up some space from C: it has eight years of business mulch clogging it up.
But I couldn't see the Ubuntu partition in that output.

Was that the complete output for fdisk -l?

Did you install Ubuntu via Wubi installer, inside Windows? Or it is a proper dual-boot setup?

---

### Post by oldos2er on 2010-11-23
If there's no Linux partition it must be Wubi.

---

### Post by sikander3786 on 2010-11-23
> **oldos2er said:**
> If there's no Linux partition it must be Wubi.
Yes indeed. And if thats the case, we have been banging our heads against the wall since the beginning of this thread 	](*,)

We should have cleared that up as soon as we started. :-)

I'll be careful next time.

---

### Post by hwuu on 2010-11-23
I don't know anything about wubi. I can boot windows, I can boot ubuntu. 

the sudo thing in its absolute entirety:

jeff@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc0dbc0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
jeff@ubuntu:~$ ^C
jeff@ubuntu:~$

---

### Post by cgroza on 2010-11-23
Your file are under /host/ in a WUBI install. Next time specify that you use WUBI. 
Its not the "sudo" thing... Its the "fdisk" thing...

---

### Post by hwuu on 2010-11-23
Looking at the link I installed from:

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

It looks like it is Wubi. It sounds like there are more than one way to dual boot.

do I need to reinstall some other way?

---

### Post by hwuu on 2010-11-24
What is WUBI? did I do something wrong?

---

### Post by Swagman on 2010-11-24
You **didn't** do *anything* wrong persay.

Wubi is a good way to do a "try install" of Ubuntu as it doesn't really change anything and can easily be deleted in the standard "windows Way" without fear of having to FixMBR in CMD

But Wubi can be prone to b0rking after Ubuntu updates.

---

