---
title: "Unable to create clone backup"
date: 2010-06-29
forum: General Help
---

### Post by rmcellig on 2010-06-29
I am trying to clone my drive to my external drive. Never had problems before. What should I do? I am pretty new to this. This is the error I received in Clonezilla. I started up from the Clonezilla CD.

Partclone v0.1.1 (Rev:304M) [http://partclone.org](http://partclone.org)
Starting to clone device (/dev/hda1) to image (-)
Reading Super Block
FS has been mounted 134547760 times without being checked
Partclone fail, please check /var/log/partclone.log !
Checking the disk space... 
(standard_in) 1: syntax error
Something went wrong!!!
Press "Enter" to continue.....

---

### Post by Austin25 on 2010-06-29
What does /var/log/partclone.log say?

---

### Post by rmcellig on 2010-06-29
I'm back into my HD now running the latest version of Ubuntu. How do I access my partclone.log file

---

### Post by Manyette on 2010-06-29
If you have downloaded some "proposed" updates, there is an uninitialized variable in the disk boot count.  A reboot should fix it, and clonezilla should then work properly.  If you are using EXT3.  I believe (but am not certain) that EXT4 is not supported in all cases.

---

### Post by macstar on 2010-06-29
i think clonezilla doesnt work with ext4. i couldnt get it to work on my installation as well.

my suggest to you is to try out the following programs:

- ghost 4 linux
- paragon backup & recovery 10


they both can handle ext4 file system.

---

### Post by rmcellig on 2010-06-29
Thanks macstar!! I am trying ghost 4 linux at the moment. Will post back if successful/ unsuccessful.

---

### Post by rmcellig on 2010-06-29
I booted up from the Ghost 4 Linux CD I created and now I am totally confused as to what to do next. Clonezilla seems to be easier to get through to do a clone backup. Is there a GUI or step by step method that I can use with Ghost 4 Linux or is there another free cloning solution that is easy to use?

---

### Post by DJonsson2008 on 2010-06-29
I've been using Gparted live disk for this sort of thing for about 2 years now, works like a charm. Not sure what the advantage with something like Clonezilla or these other tools might be. I think Gparted has been ext4 compatible since 2008.

Just boot with the Live CD go accept all the default parameters with
the CD boots and then copying partition from disk to disk is as simple as cut and paste.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by rmcellig on 2010-06-29
Thanks DJonsson2008! So I can use Gparted to clone my main Ubuntu drive to an image file on my external HD?

---

### Post by DJonsson2008 on 2010-06-29
If you have data on your external drive you may want to back it up first.

---

### Post by rmcellig on 2010-06-29
Basically all I want to do is create a clone of my main drive to an image file on my external drive. Clonezilla was working fine before so I am not sure why it is not working now so trying other solutions that are easy to use seems to be the answer for me as long as they are free, easy to use and I am able to backup to an image file.

---

### Post by DJonsson2008 on 2010-06-29
I use Gparted for making bootable clone drives but not for backing
up an image. As I find having a bootable cloned drive around much more practical and reassuring than simply having an image file. 

I keep my ubuntu partitions to 16-30 gb in size. So for instance if
I've a 250gb drive I'll partition it first with 20-40gb for Ubuntu,
then copy and paste my bootable ubuntu partition to that using
Gparted, and use the rest for data storage.

If not exactly what you had in mind. sorry for the diversion, but the objective is similar, if you are comfortable with the concept of partitioning drives then, the above method might be worth a try.

---

### Post by rmcellig on 2010-06-29
Hi DJonsson2008,

I know exactly what you are saying and I agree that it is a great way to back up your main drive. I use similar software for my Mac so that I always have a boot-able backup always available. I can't do that with the external drive that I have and that I am using for my Ubuntu image clone backup short of buying a new drive to backup to. Actually come to think of it, I might have another external drive I can use from an old PC I have.

---

### Post by rmcellig on 2010-06-29
Hi DJonsson2008,

I found an external drive that is the same size as the internal drive on my Linux PC that I want to clone.


I started up from my Parted Magic CD and I launched GParted. Now, how can I create a bootable clone. What are the steps involved?

---

### Post by DJonsson2008 on 2010-06-30
Illustrated GParted documentation on copying a partition can be found here. Scroll down to to the copy section of this doc.
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

Per my memory this is what I do.

1. Delete all partitions on target drive.

2. Copy and paste each of the source
   drive partitions to the target drive.

3. When all the copying is done and sometimes
   it takes a while - shutdown the machine
   and reboot w/o CD using the newly cloned 
   drive. F12 on some MBs will allow you to 
   select the boot drive. Sometimes I disconnect
   the original source drive to test the new clone.

4. Mark the drive as operational backup dated
   with a postit and put it in a cool dry place 
   for when needed.

5. For 10$ or less at the flea market you can get
   a 20-40gb drive. This in most cases can be enough
   for a OS partition and the swap partition. I keep
   several of these on hand, backed up, tested
   and ready to go. (There is nothing like redundant 
   operational backups).

Best to initially copy and paste, copy your partition structure exactly like the original drive from left to right.
My partitions structure looks roughly like this in Gparted
---------------------------------------------------
|OS       | DATA                             |swap|
|20GB     | 200GB                            |3GB |
---------------------------------------------------

I'm not sure if the position of the swap partition 
is critical, do replicate your working drive in 
sequence. Avoid resizing until you have booted drive.

As towards caveats, resizing with Gparted live during the copying process sometimes does not work for me, especially if making a massive resize on the OS partition. It seems better to copy & paste all the partitions first, reboot and test the drive & then re-size after. 

Once you have created a disk like this its even easier to make subsequent backups simply by copying & pasting the OS partition.

I've done this between various brands of drives, and between IDE and SATA drives, but the first time you may want to use a drive closely related in size and perhaps a matched brand/model
although I've yet to encounter any problems except on one very old small drive with outdated firmware.

Here is another instructional on the process, it is perhaps too detailed, reading it though may help. Although I should mention I've never had to do any of the grub steps they mention in the below link using more recent versions of GParted Live.
[http://ubuntuforums.org/archive/index.php/t-302717.html](http://ubuntuforums.org/archive/index.php/t-302717.html)

---

### Post by dcstar on 2010-06-30
> **rmcellig said:**
> I am trying to clone my drive to my external drive. Never had problems before. What should I do? I am pretty new to this. This is the error I received in Clonezilla. I started up from the Clonezilla CD.

Partclone v0.1.1 (Rev:304M) [http://partclone.org](http://partclone.org)
Starting to clone device (/dev/hda1) to image (-)
[B]Reading Super Block
FS has been mounted 134547760 times without being checked[/B]
Partclone fail, please check /var/log/partclone.log !
Checking the disk space... 
(standard_in) 1: syntax error
Something went wrong!!!
Press "Enter" to continue.....

I would be running a **fsck** on that partition before trying to clone it.

---

### Post by macstar on 2010-06-30
> **rmcellig said:**
> Thanks macstar!! I am trying ghost 4 linux at the moment. Will post back if successful/ unsuccessful.


i found you a good guide here:
[http://blog.tayfundogan.com/2009/07/how-to-clone-your-disk-with-g4l.html](http://blog.tayfundogan.com/2009/07/how-to-clone-your-disk-with-g4l.html)

> 
**2)  Cloning your disk to a Local Disk**

It  is easiest and probably the fastest way to clone your disk. You don't  need to set your network connection like FTP example above you just go  to raw mode and sleect click n clone. It will ask you which disk is  going to be cloned to which disk after setting this you ready to go. It  doesn't matter disk sizes and speed are different.
so you just select raw mode, then click n clone. then you select the disk. thats all. hope it helps.

---

### Post by rmcellig on 2010-06-30
Thanks Macstar!! I will try what you described above. I will post back with the results.

---

