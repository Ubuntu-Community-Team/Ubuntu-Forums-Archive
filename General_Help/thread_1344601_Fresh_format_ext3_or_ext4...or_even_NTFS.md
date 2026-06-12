---
title: "Fresh format: ext3 or ext4...or even NTFS?"
date: 2009-12-03
forum: General Help
---

### Post by Cytochromec on 2009-12-03
Hello. Ubuntu 9.10 64bit is my first Linux experience and I havent used windows 7 once in the past month of dual booting, so I decided to format and install Ubuntu fresh and get rid of NTFS altogether. However, I have heard something mixed things about ext4 causing file corruption due to some Kernal incomaptibilty (or something), so I wanted to know which way should I go? Here is my setup:

Partition Root
Partition Swap
Partition Storage (over 400GB of files of all sizes, 700MB+ and so on; currently NTFS)

1) Should I make root and storage ext3 or has all this ext4 scare settled down? 
2) Is ext3 considerably slower, what am I missing in ext4 if I choose ext3?
3) Should I keep my storage partition in the current NTFS format and ignore ext3 and 4?

Thanks mates.

---

### Post by jegerjensen on 2009-12-03
Isn't it so that an ext3 partition can be upgraded to ext4 at a later point?

---

### Post by Cytochromec on 2009-12-03
So...your saying install ext3 and upgrade later? Please elaborate.

---

### Post by akakingess on 2009-12-03
> **Cytochromec said:**
> Hello. Ubuntu 9.10 64bit is my first Linux experience and I havent used windows 7 once in the past month of dual booting, so I decided to format and install Ubuntu fresh and get rid of NTFS altogether. However, I have heard something mixed things about ext4 causing file corruption due to some Kernal incomaptibilty (or something), so I wanted to know which way should I go? Here is my setup:

Partition Root
Partition Swap
Partition Storage (over 400GB of files of all sizes, 700MB+ and so on; currently NTFS)

1) Should I make root and storage ext3 or has all this ext4 scare settled down? 
2) Is ext3 considerably slower, what am I missing in ext4 if I choose ext3?
3) Should I keep my storage partition in the current NTFS format and ignore ext3 and 4?

Thanks mates.
Almost all of those questions are personal opinion, so you will probably hear differently from different people, I haven't had a problem with ext4 yet (knock on wood) so I don't think it is as big an issue anymore, and if I could add my own 2 cents, I would make the root partition about 30GB (probably overkill, but better to have it and not need than vice versa), SWAP should be about 1.5 times or 2 times the amount of RAM (or so I have heard), but the rest I would make your /home partition, this will save all of your documents, audio, video, etc. in your home directories and if you ever have to do a reinstall (God forbid) or choose to upgrade, the installation won't even need to touch your home directories (i.e. the files you want to save). Also, double check the fact about being able to upgrade from ext3 to ext4 with no issues prior to deciding, because as I said before, I went with ext4 and haven't had any issues, and if the next build of Ubuntu "recommends" ext4, then I am already prepared. Just my humble opinion and I hope you hear from some more with some sage advice. Good luck and glad you have "officially" moved over to the good side ;)

---

### Post by jegerjensen on 2009-12-03
> **Cytochromec said:**
> So...your saying install ext3 and upgrade later? Please elaborate.

Yes, that was meant as a 4th option. I should add that **I am not an expert and cannot say what is the best option.**  

According to [http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4") it is possible to upgrade ext3 to ext4.  So sticking with ext3 today, does not mean you are stuck with it forever.

---

### Post by mixmaster on 2009-12-03
ext3 is rock solid with years of development and user experience behind it.  Unless you have very specialist requirements it will do anything you need - especially for a fairly new user.

ext4 is new.  It addresses some specific limitations of ext3 generally only encountered by power users and commercial installations.  There are still a few reports of data corruption around but it is difficult to see any major issues.  It is also slightly faster.  Some ext3 tools are still not available for ext4.

There is a procedure for migrate-in-place to ext4 if you find a need for it later.  You would need to boot from a CD or USB stick to apply it to the root filesystem.

ntfs has no place on an all-linux system.  Although linux can safely read and write to this fs it is not fully compatible at the ownership/file-permissions level with the linux model and even the filename conventions are different - there are pathological cases where two distinct linux files will end up sharing a name on ntfs.  Use ntfs only on drives shared with Win.

---

### Post by zaphod777 on 2009-12-03
As far as the external storage goes if you need to swap between Windows and Linux your options are:

1. NTFS - Linux can read and write to it but sometimes there are issues.
2. FAT32 - works pretty well but has a max file size of 4 GB this is a big limitation and there is no file security at all.
3. Ext3 - There is a Windows driver you can install so Windows can you use it and it natively works in Linux.
4. Ext4 - No Windows driver and older linux systems can't read it.
5. XFS - great file system can have exabyte file sizes but again is not Windows friendly.

I currently have a 1TB HDD connected to my router as a NAS using XFS.
I have a single 80 USB HDD formated in NTFS but it is only used to transfer files to other PC's and has no critical info on it so if it gets corrupted I won't lose any sleep if I need to format it.

If I had a large drive with critical data connected to my pc I think I would use Ext3 for better compatibility with other systems.

my internal HDD is using Ext4 as it is in the default install of 9.10.

---

### Post by akakingess on 2009-12-03
> **zaphod777 said:**
> As far as the external storage goes if you need to swap between Windows and Linux your options are:

1. NTFS - Linux can read and write to it but sometimes there are issues.
2. FAT32 - works pretty well but has a max file size of 4 GB this is a big limitation and there is no file security at all.
3. Ext3 - There is a Windows driver you can install so Windows can you use it and it natively works in Linux.
4. Ext4 - No Windows driver and older linux systems can't read it.
5. XFS - great file system can have exabyte file sizes but again is not Windows friendly.

I currently have a 1TB HDD connected to my router as a NAS using XFS.
I have a single 80 USB HDD formated in NTFS but it is only used to transfer files to other PC's and has no critical info on it so if it gets corrupted I won't lose any sleep if I need to format it.

If I had a large drive with critical data connected to my pc I think I would use Ext3 for better compatibility with other systems.

my internal HDD is using Ext4 as it is in the default install of 9.10.
If I read the original post correctly, the OP is dumping Windows and going 100% Ubuntu.

---

### Post by Cytochromec on 2009-12-03
So when we say ext4 is faster, is this noticeable? Are we implying that ext3 is slow in any way? Also, I have never had file corruption with NTFS, ever. Would ext3 give me that level of stability?

---

### Post by zaphod777 on 2009-12-03
> **akakingess said:**
> If I read the original post correctly, the OP is dumping Windows and going 100% Ubuntu.

But doesn't mean that every ones of his friends and family are. If it is a small USB HDD he may need to take it on the go or something like that.


I would use Ext3 if he doesn't need to easily connect to any Windows machines in the future.

---

### Post by akakingess on 2009-12-03
> **zaphod777 said:**
> But doesn't mean that every ones of his friends and family are. If it is a small USB HDD he may need to take it on the go or something like that.


I would use Ext3 if he doesn't need to easily connect to any Windows machines in the future.

Good point, hadn't thought of that...

---

### Post by zaphod777 on 2009-12-03
> **Cytochromec said:**
> So when we say ext4 is faster, is this noticeable? Are we implying that ext3 is slow in any way? Also, I have never had file corruption with NTFS, ever. Would ext3 give me that level of stability?


Ext4 is supposed to be faster than Ext3 but I haven't really noticed. Linux doesn't work as well as MS with ntfs just last week i was helping someone that corrupted the whole hdd after a power interruption and had to format the whole drive. 

[http://ubuntuforums.org/showthread.php?p=8395790#post8395790](http://ubuntuforums.org/showthread.php?p=8395790#post8395790)

Also the built in tools in Linux are designed to for Linux file systems so using a native format is always better.

As far as Stability goes Ext3 has been around for years and proved to be very stable. But you should always have a backup just in case all HDD do fail at some time.

---

### Post by Zoot7 on 2009-12-03
Ext4 from Kernel 2.6.28 on supposedly is perfectly stable. I've been using Ext4 since Jaunty and I haven't had any problems yet.
However my external hard drives are formatted to Ext3, merely because there's too much data there to risk changing it to Ext4.

As regards which file system to choose if you want both Windows and Ubuntu to access it then format it to ntfs, if it's Ubuntu only use Ext3. I do find Ext4 faster than Ext3, but I wouldn't use it for external storage as long as there's report of data corruption in the wild (granted I've never read anything to suggest anyone has had problems with it).

---

### Post by Cytochromec on 2009-12-03
> **Zoot7 said:**
> Ext4 from Kernel 2.6.28 on supposedly is perfectly stable. I've been using Ext4 since Jaunty and I haven't had any problems yet.
However my external hard drives are formatted to Ext3, merely because there's too much data there to risk changing it to Ext4.

As regards which file system to choose if you want both Windows and Ubuntu to access it then format it to ntfs, if it's Ubuntu only use Ext3. I do find Ext4 faster than Ext3, but I wouldn't use it for external storage as long as there's report of data corruption in the wild (granted I've never read anything to suggest anyone has had problems with it).

So the newer 2.6.31 Kernel is not as "perfectly stable?"

Also, this is for my laptop. My home network has xp on them, but I dont plan to be interacting the two computers, ever. I have an external with my data backed up, and thats on NTFS. From all the replies so far, it seems as though ext3 might be the best way to go. 

One more thing. Someone mentioned Linux isnt as good as MS with NTFS. Is this a can of beans waiting to be opened or is this well known? Im not trying to open a can of beans, Im just a Linux newb.

---

### Post by zaphod777 on 2009-12-03
> **Cytochromec said:**
>  I have an external with my data backed up, and thats on NTFS. From all the replies so far, it seems as though ext3 might be the best way to go. 

One more thing. Someone mentioned Linux isnt as good as MS with NTFS. Is this a can of beans waiting to be opened or is this well known? Im not trying to open a can of beans, Im just a Linux newb.

Don't you know this site is all about the beans ;-) 

Running a native format is always best Microsoft has not open sourced NTFS so even though it works we don't have access to the internals on how it really works inside.

It can be a pain if the NTFS file system gets flagged as dirty from not cleanly unmounting it. 

Windows will deal with it automatically but you have to run some command line stuff to mark it clean in Linux.

Even in Windows I have had to run check disk to fix pc's that no longer boot because of the file system getting messed up.

If it won't put you out too much then I would switch to Ext3 if it will be a pain you could just wait until you buy a larger drive and then use Ext3.

I know pretty soon USB 3.0 drives will be available and I am salivating.

but you need to get a USB 3.0 card for those. 

Either way NTFS is probably "ok" for now just keep in mind you should always unmount it don't just unplug it if possible.

---

### Post by Zoot7 on 2009-12-03
> **Cytochromec said:**
> So the newer 2.6.31 Kernel is not as "perfectly stable?"
No I meant everything since 2.6.28 has been stable with Ext4 including 2.6.29 up to 2.6.31. I've Ext4 for both my home partition and system partition, no issues at all.

> **Cytochromec said:**
> Also, this is for my laptop. My home network has xp on them, but I dont plan to be interacting the two computers, ever. I have an external with my data backed up, and thats on NTFS. From all the replies so far, it seems as though ext3 might be the best way to go. 
Yup, Ext3 has been around quite a while now, and is extremely stable.

> **Cytochromec said:**
> One more thing. Someone mentioned Linux isnt as good as MS with NTFS. Is this a can of beans waiting to be opened or is this well known? Im not trying to open a can of beans, Im just a Linux newb.
Well Windows will always be the best thing to deal with NTFS partitions since ntfs was designed for Windows.
However the read and write support of Linux to Ntfs is pretty flawless about now, ever since the Ntfs-3g driver.
The only problem are operations like defragmentation and error correcting, you're far better off you use Windows for those.

---

