---
title: "Ubuntu &gt; Windows ?"
date: 2011-12-14
forum: General Help
---

### Post by $ixtus on 2011-12-14
Greetings, said the noob Sixtus on the ubuntu forum.
I am currently running the OS from the CD AGAIN! from my Acer [5553G]("http://www.expertreviews.co.uk/laptops/279271/acer-aspire-5553g/specifications") laptop so i hope you accept some rough language expression during my explanation and search for help. 

Now couple of weeks ago i just got tired of Windows. And decided to convert to something else, and no way that i am touching a Apple product. So now that Linux has come with a new 11.10 ubuntu it was quite interesting. I decided to give it a try! and boy was i happy with the looks of it ;)
Just gorgeous looks and function.

So, during these couple of weeks i had my wonderful ubuntu i even read and learned some new tricks, like ...whats it called... Conky yes!, some commands in Terminal and some more. Now remember EVERYTHING is new to me in ubuntu so i am learning even this second about this Osystem. But as a engineer student i love to learn new things. 
So far i am part happy with this Ubuntu. 

Now let me come to the point, the ONLY problem so far is that I am tired of reinstalling this OS every time it doesn't want to BOOT properly! after some update or what ever it up! I dont know what else to do besides go back to Windows! ( in this case its gonna be XP or 95 ) 
But i REALLY like Ubuntu and am just getting used to it, and i would really like to get some feedback by the Linux pioneers on what i can do...and what is causing those boot problems ?
Is there a boot fix file or something for a usb? easyer fix than reinstall every time ??? 
Edit : forgot to mention, i think i downloaded 64 bit buntu since my W7 was 64bit, is that maybe causing problems since its not 32?
Best regards Six!




And my current problem : 
[http://ubuntuforums.org/showthread.php?p=11537367#post11537367](http://ubuntuforums.org/showthread.php?p=11537367#post11537367)

Here is my Ubuntu :

[IMG]http://img831.imageshack.us/img831/8600/19460210150394800336008.jpg[/IMG]

---

### Post by WorMzy on 2011-12-14
Please use the default font, that one is hideous and hard to read.

You don't have to reinstall Ubuntu just because it doesn't boot, in the same way that you don't have to replace a house because the door won't open.

Now I can't tell you why your Ubuntu periodically refuses to boot, at least not without some more information. The next time you have the problem, boot a liveCD/USB of Ubuntu, and run the following script: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Instructions on how to use it are on this page: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by matt_symes on 2011-12-14
Hi

It seem i have just posted in your other thread; pretty much the same instructions as Wormzy.

Please change the font in your post #1. It hurts my eyes and is very difficult to read.

EDIT: Thanks for changing the font. You must have done that while i was writing this post.

Kind regards

---

### Post by $ixtus on 2011-12-14
> **WorMzy said:**
>  The next time you have the problem, boot a liveCD/USB of Ubuntu, and run the following script: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Instructions on how to use it are on this page: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Now you see.... you didnt read my text carefully. this is that NEXT time, if you read my first sentence you would understand that i am running TRY version ubuntu from CD
My ubuntu is still Not working. 

I can add that most of the times i Shut Down ubuntu it restarts fine mostly BUT when i close the screen and it shuts down , its mostly than the problem appears. but that just a guess  its not something im 100 percent sure of . 


> **WorMzy said:**
>  boot a liveCD/USB of Ubuntu,

and what does this mean ?

---

### Post by $ixtus on 2011-12-14
> **matt_symes said:**
> Hi

It seem i have just posted in your other thread; pretty much the same instructions as Wormzy.


Kind regards

appreciate the fast reply , i hope your help can provide with  solve of this problem

---

### Post by Bromden on 2011-12-14
With ```
uname -m
``` into terminal you can see your architecture.

When do you start having problems? After the first upgrade of Ubuntu?

If abandoning Unity is not a problem for you, I would suggest to try 10.10 instead of 11.10.

---

### Post by Mark Phelps on 2011-12-14
If the problem is happening when you close the laptop, then it's related in some way to SUSPEND actions -- which means it's not shutting down properly such that, when you next open the laptop, it's not able to boot properly.

SUSPEND is one of those things I've never been able to get to work on laptops, so sorry, don't have a solution for you ...

But there are others that frequent this section, and once you actually do us the favor of running the script and posting the results, I am sure they will be glad to help.

---

### Post by $ixtus on 2011-12-14
i think its the 3rd update this time that screwed it.

but remember first time its not and update at all that deformed my boot system , it sometimes just happens for no reason like if i close my screen and try to start it again... and like i said before it most of the time works when i use Shut down to close my laptop and not just close the screen

---

### Post by WorMzy on 2011-12-14
> **$ixtus said:**
> Now you see.... you didnt read my text carefully. this is that NEXT time

So where's the results from the script? :)

The LiveCD is the CD you're booted into.

---

### Post by $ixtus on 2011-12-14
Let me try to add that script and hopefully we can take the next step into/outof this problem

---

### Post by matt_symes on 2011-12-14
Hi


> **$ixtus said:**
> Now you see.... you didnt read my text carefully. this is that NEXT time, if you read my first sentence you would understand that i am running TRY version ubuntu from CD
My ubuntu is still Not working. 

I can add that most of the times i Shut Down ubuntu it restarts fine mostly BUT when i close the screen and it shuts down , its mostly than the problem appears. but that just a guess  its not something im 100 percent sure of . 
> 
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init = bootarg.Is this the exact error message you are getting ? Is this the install on your hard drive that is giving you this error because you usually do not get that error if you are > running TRY version ubuntu from CD and it is running from the CD only.

What it means is it cannot mount your root filing system. That may be a problem with grub or may be a problem with the partitions filing system (it may be some other problems as well). Running the boot info script will shed more light on what is going on.

If this keeps happening to you when you shut down the computer then you have another problem as well.

> and what does this mean ?Wormzy means running a try version of ubuntu. That is also called running or booting a LiveCD/USB.

Run the try version of Ubuntu from a LiveCD/USB, download and run the boot info script.

Kind regards

---

### Post by $ixtus on 2011-12-14
[U][B]Is this any help ?? 

[/B][/U]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,238,206,463 1,238,204,416  83 Linux
/dev/sda2       1,238,208,510 1,250,263,039    12,054,530   5 Extended
/dev/sda5       1,238,208,512 1,250,263,039    12,054,528  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        265eeef9-bdfa-42df-897f-a36839eede48   ext4       
/dev/sda5        2cbccbe2-fdcc-4d32-87a7-111fe9d90916   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by WorMzy on 2011-12-14
All right, looks like something's gone wrong with your filesystem.

Run

```
sudo e2fsck -p /dev/sda1
```

---

### Post by $ixtus on 2011-12-14
ubuntu@ubuntu:~$ sudo e2fsck -p /dev/sda1
/dev/sda1: recovering journal
/dev/sda1: Note: if several inode or block bitmap blocks or part
of the inode table require relocation, you may wish to try
running e2fsck with the '-b 32768' option first.  The problem
may lie only with the primary block group descriptors, and
the backup block group descriptors may be OK.

/dev/sda1: Block bitmap for group 384 is not in group.  (block 1836068706)


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)

---

### Post by WorMzy on 2011-12-14
Well well, we're into uncharted territory now. You may want to wait for a second opinion rather than following my advice directly from this point onwards.

It only mentioned one block bitmap block, so I don't think you need to run the "-b 32768" command. I'd wait to see what the fsck command says first:

```
sudo fsck /dev/sda1
```

---

### Post by $ixtus on 2011-12-14
> **WorMzy said:**
> 
```
sudo fsck /dev/sda1
```
  
should i run that command or should i wait to see what other people have to say ?

---

### Post by WorMzy on 2011-12-14
Like I said, that's up to you.

I don't think you need to do that "-b 32768" command before you fsck, but maybe you do. Alternatively, maybe running the "-b 32768" command before you fsck will do more harm than good.

It's not something I have personal experience with, so I can only say what *I'd* do.

---

### Post by $ixtus on 2011-12-14
ill give it a little more time to see what other people have to add...

by looking at the text i posted above one cant tell what problem is ?

---

### Post by matt_symes on 2011-12-14
Hi

You have some major filing system corruption going on there.

Personally what i would do is run fsck with the backup super block but using the -n switch to see what it would do.

```
fsck -n -b 32768 /dev/sda1
```Posting back the output may give some direction.

Kind regards

---

### Post by $ixtus on 2011-12-14
> **matt_symes said:**
> 

You have some major filing system corruption going on there.

I cant believe that!!! I didnt do anything different than any other time i normally use my laptop! 
this is what pisses me off, for no reason things just get corrupted 
anyways here is what i got from the Code  : 

ubuntu@ubuntu:~$ fsck -n -b 32768 /dev/sda1
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Permission denied while trying to open /dev/sda1
You must have r/o access to the filesystem or be root

---

### Post by matt_symes on 2011-12-14
Hi

> **$ixtus said:**
> I cant believe that!!! I didnt do anything different than any other time i normally use my laptop! 
this is what pisses me off, for no reason things just get corrupted 
anyways here is what i got from the Code  : 

ubuntu@ubuntu:~$ fsck -n -b 32768 /dev/sda1
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Permission denied while trying to open /dev/sda1
You must have r/o access to the filesystem or be root

Sorry try

```
sudo fsck -n -b 32768 /dev/sda1 
```

Post back results.

Kind regards

---

### Post by mbuell on 2011-12-14
> **$ixtus said:**
> ....  i am running TRY version ubuntu from CD
My ubuntu is still Not working. 

I can add that most of the times i Shut Down ubuntu it restarts fine mostly BUT when i close the screen and it shuts down , its mostly than the problem appears. but that just a guess  its not something im 100 percent sure of . 


Well - one thing to note right here - if I read this correctly sometimes you are having this problem when you SHUT DOWN your computer by CLOSING the lid. Am I right? Your laptop tries to go into suspend or sleep mode when you close the lid. A previous poster mentioned this - suspend and sleep mode in linux are flaky with some laptops. Metaphorically speaking, you could be getting file system problems because your hardware is arguing with your OS when you close the lid - throwing things at each other kind like an old married couple. 

I think it might simplify your life for now if you shutdown by telling Ubuntu to shutdown before you close the lid. After you get this boot issue ironed out, see if you can google a sleep mode solution for your laptop. 
My $.02
Good luck.

---

### Post by $ixtus on 2011-12-14
> **matt_symes said:**
> Hi
```
sudo fsck -n -b 32768 /dev/sda1 
```Post back results.
Kind regards
wow matt... lot of things appeared 
many other things appeared as well but i cant scroll back up to see them. 
here are all i could scroll to see that appeared. 

```
Directories count wrong for group #3152 (0, counted=1).
Fix? no

Free inodes count wrong for group #3168 (8192, counted=3784).
Fix? no

Free inodes count wrong for group #3184 (8192, counted=4579).
Fix? no

Free inodes count wrong for group #3200 (8192, counted=8164).
Fix? no

Directories count wrong for group #3200 (0, counted=12).
Fix? no

Free inodes count wrong for group #3232 (8192, counted=8190).
Fix? no

Free inodes count wrong for group #3248 (8192, counted=8191).
Fix? no

Free inodes count wrong for group #3264 (8192, counted=8148).
Fix? no

Directories count wrong for group #3264 (0, counted=1).
Fix? no

Free inodes count wrong for group #3456 (8192, counted=8191).
Fix? no

Free inodes count wrong for group #3488 (8192, counted=8191).
Fix? no

Free inodes count wrong for group #3520 (8192, counted=8100).
Fix? no

Directories count wrong for group #3520 (0, counted=4).
Fix? no

Free inodes count wrong for group #3808 (8192, counted=8191).
Fix? no

Directories count wrong for group #3808 (0, counted=1).
Fix? no

Free inodes count wrong for group #3840 (8192, counted=63).
Fix? no

Directories count wrong for group #3840 (0, counted=566).
Fix? no

Free inodes count wrong for group #3841 (8192, counted=6306).
Fix? no

Directories count wrong for group #3841 (0, counted=33).
Fix? no

Free inodes count wrong for group #3856 (8192, counted=4534).
Fix? no

Directories count wrong for group #3856 (0, counted=595).
Fix? no

Free inodes count wrong for group #3872 (8192, counted=2545).
Fix? no

Directories count wrong for group #3872 (0, counted=593).
Fix? no

Free inodes count wrong for group #3888 (8192, counted=1872).
Fix? no

Directories count wrong for group #3888 (0, counted=593).
Fix? no

Free inodes count wrong for group #3904 (8192, counted=0).
Fix? no

Directories count wrong for group #3904 (0, counted=561).
Fix? no

Free inodes count wrong for group #3905 (8192, counted=7081).
Fix? no

Directories count wrong for group #3905 (0, counted=32).
Fix? no

Free inodes count wrong for group #3920 (8192, counted=4264).
Fix? no

Directories count wrong for group #3920 (0, counted=593).
Fix? no

Free inodes count wrong for group #3936 (8192, counted=5473).
Fix? no

Directories count wrong for group #3936 (0, counted=593).
Fix? no

Free inodes count wrong for group #3952 (8192, counted=4918).
Fix? no

Directories count wrong for group #3952 (0, counted=593).
Fix? no

Free inodes count wrong for group #3968 (8192, counted=2812).
Fix? no

Directories count wrong for group #3968 (0, counted=593).
Fix? no

Free inodes count wrong for group #3969 (8192, counted=5545).
Fix? no

Free inodes count wrong for group #3984 (8192, counted=3966).
Fix? no

Directories count wrong for group #3984 (0, counted=593).
Fix? no

Free inodes count wrong for group #4000 (8192, counted=3463).
Fix? no

Directories count wrong for group #4000 (0, counted=547).
Fix? no

Free inodes count wrong for group #4016 (8192, counted=252).
Fix? no

Directories count wrong for group #4016 (0, counted=420).
Fix? no

Free inodes count wrong for group #4017 (8192, counted=3457).
Fix? no

Directories count wrong for group #4017 (0, counted=151).
Fix? no

Free inodes count wrong for group #4018 (8192, counted=3213).
Fix? no

Directories count wrong for group #4018 (0, counted=22).
Fix? no

Free inodes count wrong for group #4019 (8192, counted=6947).
Fix? no

Free inodes count wrong for group #4032 (8192, counted=0).
Fix? no

Directories count wrong for group #4032 (0, counted=529).
Fix? no

Free inodes count wrong for group #4033 (8192, counted=1163).
Fix? no

Directories count wrong for group #4033 (0, counted=64).
Fix? no

Free inodes count wrong for group #4048 (8192, counted=0).
Fix? no

Directories count wrong for group #4048 (0, counted=534).
Fix? no

Free inodes count wrong for group #4049 (8192, counted=4865).
Fix? no

Directories count wrong for group #4049 (0, counted=65).
Fix? no

Free inodes count wrong for group #4064 (8192, counted=2964).
Fix? no

Directories count wrong for group #4064 (0, counted=599).
Fix? no

Free inodes count wrong for group #4080 (8192, counted=1820).
Fix? no

Directories count wrong for group #4080 (0, counted=599).
Fix? no

Free inodes count wrong for group #4096 (8192, counted=3000).
Fix? no

Directories count wrong for group #4096 (0, counted=599).
Fix? no

Free inodes count wrong for group #4112 (8192, counted=3782).
Fix? no

Directories count wrong for group #4112 (0, counted=599).
Fix? no

Free inodes count wrong for group #4128 (8192, counted=2725).
Fix? no

Directories count wrong for group #4128 (0, counted=599).
Fix? no

Free inodes count wrong for group #4144 (8192, counted=3363).
Fix? no

Directories count wrong for group #4144 (0, counted=599).
Fix? no

Free inodes count wrong for group #4160 (8192, counted=6069).
Fix? no

Directories count wrong for group #4160 (0, counted=599).
Fix? no

Free inodes count wrong for group #4176 (8192, counted=6357).
Fix? no

Directories count wrong for group #4176 (0, counted=599).
Fix? no

Free inodes count wrong for group #4192 (8192, counted=4702).
Fix? no

Directories count wrong for group #4192 (0, counted=599).
Fix? no

Free inodes count wrong for group #4208 (8192, counted=4391).
Fix? no

Directories count wrong for group #4208 (0, counted=599).
Fix? no

Free inodes count wrong for group #4224 (8192, counted=6494).
Fix? no

Directories count wrong for group #4224 (0, counted=599).
Fix? no

Free inodes count wrong for group #4240 (8192, counted=3031).
Fix? no

Directories count wrong for group #4240 (0, counted=599).
Fix? no

Free inodes count wrong for group #4256 (8192, counted=6181).
Fix? no

Directories count wrong for group #4256 (0, counted=599).
Fix? no

Free inodes count wrong for group #4272 (8192, counted=6429).
Fix? no

Directories count wrong for group #4272 (0, counted=599).
Fix? no

Free inodes count wrong for group #4288 (8192, counted=6149).
Fix? no

Directories count wrong for group #4288 (0, counted=599).
Fix? no

Free inodes count wrong for group #4304 (8192, counted=324).
Fix? no

Directories count wrong for group #4304 (0, counted=599).
Fix? no

Free inodes count wrong for group #4320 (8192, counted=4659).
Fix? no

Directories count wrong for group #4320 (0, counted=599).
Fix? no

Free inodes count wrong for group #4336 (8192, counted=1914).
Fix? no

Directories count wrong for group #4336 (0, counted=599).
Fix? no

Free inodes count wrong for group #4352 (8192, counted=3285).
Fix? no

Directories count wrong for group #4352 (0, counted=599).
Fix? no

Free inodes count wrong for group #4368 (8192, counted=5829).
Fix? no

Directories count wrong for group #4368 (0, counted=599).
Fix? no

Free inodes count wrong for group #4384 (8192, counted=3752).
Fix? no

Directories count wrong for group #4384 (0, counted=599).
Fix? no

Free inodes count wrong for group #4400 (8192, counted=6133).
Fix? no

Directories count wrong for group #4400 (0, counted=599).
Fix? no

Free inodes count wrong for group #4416 (8192, counted=6253).
Fix? no

Directories count wrong for group #4416 (0, counted=599).
Fix? no

Free inodes count wrong for group #4432 (8192, counted=7702).
Fix? no

Directories count wrong for group #4432 (0, counted=168).
Fix? no

Free inodes count wrong for group #4480 (8192, counted=3776).
Fix? no

Directories count wrong for group #4480 (0, counted=584).
Fix? no

Free inodes count wrong for group #4496 (8192, counted=4487).
Fix? no

Directories count wrong for group #4496 (0, counted=587).
Fix? no

Free inodes count wrong for group #4512 (8192, counted=4340).
Fix? no

Directories count wrong for group #4512 (0, counted=586).
Fix? no

Free inodes count wrong for group #4528 (8192, counted=6846).
Fix? no

Directories count wrong for group #4528 (0, counted=275).
Fix? no

Free inodes count wrong for group #4640 (8192, counted=8191).
Fix? no

Free inodes count wrong (38698997, counted=38251145).
Fix? no


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

/dev/sda1: ********** WARNING: Filesystem still has errors **********

/dev/sda1: 11/38699008 files (4827.3% non-contiguous), 2479360/154775552 blocks
Error writing block 1 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 2 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 3 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 4 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 5 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 6 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 7 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 8 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 9 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 10 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 11 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 12 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 13 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 14 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 15 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 16 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 17 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 18 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 19 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 20 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 21 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 22 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 23 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 24 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 25 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 26 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 27 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 28 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 29 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 33 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 34 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 35 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 36 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 37 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 30 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 31 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 32 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 33 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 34 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 35 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 36 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 37 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 30 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 31 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 32 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 33 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 34 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 35 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 36 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 37 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 30 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 31 (Attempt to write block from filesystem resulted in short write).  Ignore error? no

Error writing block 32 (Attempt to write block from filesystem resulted in short write).  Ignore error? no
 
```

> **mbuell said:**
> 

I think it might simplify your life for now if you shutdown by telling Ubuntu to shutdown before you close the lid. After you get this boot issue ironed out, see if you can google a sleep mode solution for your laptop. 
My $.02
Good luck.
Yea i am feeling you on this one man. 
thanks for the input

---

### Post by matt_symes on 2011-12-14
Hi

Alright. If you have any important data on that partition make an image of the partition now.

Try to run fsck using the backup superblock. From the CD

```
sudo fsck -y -b 32768 /dev/sda1
```

Cross your fingers and hope for the best. 

Kind regards

---

### Post by mbuell on 2011-12-14
Re: making a disk image - always a good idea - you have a couple of options to do this:

1: Make a backup instead. Back up any documents and precious files - to whatever and however you normally do this - with the massive size of thumb drives today, copying your files is a no-brainer. You might have to reinstall some favorite programs - but I think you are doing that anyway. 

Or

2. Do a real disk image. In the windows world the gold standard once upon a time was Ghost. Today there are several linux utilities that do the same job, quite nicely. However - you often need several of them - and they require a learning curve - which we do not need at the moment - SO, check out clonezilla. All free. Clonezilla uses a few of those Linux utilities for you. 

You can make a clonezilla cd, boot from it, and clone away. The menus were obviously not written by a native English speaker, but they are still pretty good at getting you to the objective.

---

### Post by $ixtus on 2011-12-15
> **matt_symes said:**
> Hi

Alright. If you have any important data on that partition make an image of the partition now.

Try to run fsck using the backup superblock. From the CD

```
sudo fsck -y -b 32768 /dev/sda1
```Cross your fingers and hope for the best. 

Kind regards


What is this going to do ? 

And am i going to loose all my appearance of the ubuntu , is it going to be set back to standard ??

---

### Post by Mark Phelps on 2011-12-15
I told you WAY BACK in post #7 that this was most likely a SUSPEND problem.  As long as you have laptop setup to suspend when you close the lid, you're going to continue to get this filesystem corruption.

So, you have TWO problems to fix:
1) Current filesystem corruption -- fsck will likely do that for you when you get it to run right
2) Suspend -- you need to DISABLE this so that suspend no longer kicks in.

---

### Post by $ixtus on 2011-12-15
> **matt_symes said:**
> Hi

Alright. If you have any important data on that partition make an image of the partition now.

Try to run fsck using the backup superblock. From the CD

```
sudo fsck -y -b 32768 /dev/sda1
```Cross your fingers and hope for the best. 

Kind regards

My future Ubuntu Jedi  master! =D>
Thank you for the save matt it worked perfectly  


From now on i will only shut it down before closing screen .

Regards Six !

---

### Post by $ixtus on 2011-12-17
And than it happened again...this time the firefox didnt want to load so i restarted the pc 
and i got the message something like : 
ubuntu critical error I Ignore S Skip  M Manual recovery
and i think i pressed I because Fix application didnt appear. so didnt know if i should wait for it to load or if i should press I  S or M i dont know how to manual recover anyways 

but anyways here is what i have get from source forge 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,238,206,463 1,238,204,416  83 Linux
/dev/sda2       1,238,208,510 1,250,263,039    12,054,530   5 Extended
/dev/sda5       1,238,208,512 1,250,263,039    12,054,528  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        265eeef9-bdfa-42df-897f-a36839eede48   ext4       
/dev/sda5        2cbccbe2-fdcc-4d32-87a7-111fe9d90916   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 265eeef9-bdfa-42df-897f-a36839eede48
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 265eeef9-bdfa-42df-897f-a36839eede48
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 265eeef9-bdfa-42df-897f-a36839eede48
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 265eeef9-bdfa-42df-897f-a36839eede48
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=265eeef9-bdfa-42df-897f-a36839eede48 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 265eeef9-bdfa-42df-897f-a36839eede48
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=265eeef9-bdfa-42df-897f-a36839eede48 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 265eeef9-bdfa-42df-897f-a36839eede48
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=265eeef9-bdfa-42df-897f-a36839eede48 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 265eeef9-bdfa-42df-897f-a36839eede48
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=265eeef9-bdfa-42df-897f-a36839eede48 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 265eeef9-bdfa-42df-897f-a36839eede48
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=265eeef9-bdfa-42df-897f-a36839eede48 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 265eeef9-bdfa-42df-897f-a36839eede48
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=265eeef9-bdfa-42df-897f-a36839eede48 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 265eeef9-bdfa-42df-897f-a36839eede48
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 265eeef9-bdfa-42df-897f-a36839eede48
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=265eeef9-bdfa-42df-897f-a36839eede48 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2cbccbe2-fdcc-4d32-87a7-111fe9d90916 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-13-generic               1
               =                boot/initrd.img-3.0.0-14-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  2
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    2

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by matt_symes on 2011-12-17
Hi

I'll have a look at the bootscript text in a moment but first i want you to check the SMART status of your hard drive just to check it's not failing.

You will need to boot into a liveCD/USB to do this.

Start up disk utility and select the hard drive in the left hand pane.

In the right hand pane select the 'smart data' button. In the new window that appears select the 'run self test' option and select the extended test. This will take a while so go do something else.

Post back the results with a screen shot.

It will not fix your drive but it will highlight any issues on the drive.

If the SMART option is not availiable then check in the BIOS to see if there is an option to enable it.

Not all drives have SMART functionality so if you cannot find a way to enable it then do not worry.

Kind regards

---

### Post by $ixtus on 2011-12-17
Hi matt

thanks again , running selftest as we speak

btw how do i know when its finished ?


nvm i see it now ...the process

---

### Post by $ixtus on 2011-12-17
Its finished 

Power cycles : 350 
Bad sectors : None 
Overall assessment : Disk is healthy


but not all assets where green under 
most of them saying N/A

---

### Post by matt_symes on 2011-12-18
Hi

> **$ixtus said:**
> Its finished 

Power cycles : 350 
Bad sectors : None 
Overall assessment : Disk is healthy


but not all assets where green under 
most of them saying N/A

That looks fine above.

You will need to run fsck again to repair the filing system as you did before from a live cd.

> And than it happened again...this time the firefox didnt want to load so i restarted the pc 

How did you restart you PC. Did you just switch it off using the power button or did you shutdown correctly ?

If you PC hangs you can try the magic key combination to shutdown safely.

Press AltGr + SysRq at the same time and keep the pressed. Then hit 

r e s i u o

one after another leaving 3 seconds or so between each key press. That should switch off the PC gracefully as long at the kernel has not crashed on you.

We need to find out why you are getting file system corruption but to do that we may need to look into the logs and see what is going on in your system.

Kind regards

---

### Post by $ixtus on 2011-12-18
Hi matt 

I will try to run fsck and hope for the best. 
I shut the computer normanlly using shut down function

But i think when i started it up again it appeared that it had some error ... and asked me if i wanted to I (ignore )  S (skip )   M (manual recover )
and sometimes F ( fix appears ) but not this time

Should i let it stay and load for a while or what ? Because i pressed Ignore and than it got stuck and i shut down laptop with Power button by holding it down. 


If it continiue to happen i will keep posting boot Logs


thank you again 

Regards Six

---

### Post by matt_symes on 2011-12-20
Hi

I'm not sure of the boot logs will really help as your filing looks fine from the scripts.

For some reason it does not appear to be syncing correctly when you shut down you computer.

As i said, if it freezes use the magic key combination to shutdown.

If it keeps happening then it may be worth looking in dmesg logs to see if there is some problem there.

Do you have sata3 drives or anything like that ?

Kind regards

---

### Post by $ixtus on 2011-12-22
it worked again...
this time im having problems with my touch pad, it keeps disabling itself , than i have to run synaptics and only sometimes synap opens and mouse works fin again , tapping Fn + F7 mostly doesnt do much help. 


and about sata 3 im not sure , due ita a laptop havent checked up init


regards six

---

### Post by $ixtus on 2011-12-30
problems...again!
 
like same time i had problems loading into ubuntu, i was loging in but when ubuntu with loading dots appeared nothing happened ....the dots whernt loading at all they where just white without change. 
 
so i ran the fsck or what its called and fixed the boot 
 
but now the problem it that when i enter my password the desktop appears with only wallpaper and nothing else , i can only right click on the desktop and change background and what not. But when i try to go futher via desktop change to adwanced settings i am not able to click on any of the choices ...
 
what can this problem be .

---

### Post by matt_symes on 2011-12-30
Hi

> what can this problem be .I think all these problems are related and i think there is an issue with your hard disk.

Let's run an extended test on the drive to make sure it is alright.

Boot into a LiveCD/USB again, open a terminal and type

```
sudo apt-get install smartmontools
```(If prompted with any ok dialogs then hit tab to get to the <ok> and then press enter)

When installed run a test.

```
sudo smartctl -t long /dev/sda
```It will take some time so go and have a drink or something.

When it has finished, get a report of the test by typing
```

sudo smartctl -a /dev/sda
```Post the report back here.

Kind regards

---

### Post by $ixtus on 2011-12-30
hi budd
but iv alredy checked the hdd when you told me ...and it all seemed to be fine , but all aside i will do what you told me above
 
 
six

---

### Post by $ixtus on 2011-12-31
ok so i tryed to install what you told me and after i press (y) for install some weired message appeared in terminal with gray background something about some email something to choose where to get sent message and   ... in the bottom it said  >> ok << 
Now i couldnt  do anything in this window. no typing , no selecting or anything . 

and i tryed to install it by typing 
sudo apt-get install smartmontools 
several time but same message appeared . now it says this 

ubuntu@ubuntu:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  dovecot-common resolvconf postfix-cdb gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  bsd-mailx postfix smartmontools
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

---

### Post by matt_symes on 2012-01-02
Hi
> 
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

Did you have software-center of update manager running while trying to install the software ?

If you did then close them and try to install again. If not a reboot should fix that issue.

I want to see what the drive thinks of its own status.

Kind regards

---

### Post by $ixtus on 2012-01-03
Ok 
so it worked this time 
The test is running but i didnt know what choice to make when it asked me for some mail configuration. 
So i chose '' No Configuration''

and the schedule started  and now it seems it is going to take about two hours

---

### Post by $ixtus on 2012-01-03
here is what i got 

```
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD6400BEVT-00A0RT0
Serial Number:    WD-WX71C5057710
LU WWN Device Id: 5 0014ee 6aafc5cd9
Firmware Version: 01.01A01
User Capacity:    640,135,028,736 bytes [640 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Jan  3 19:27:19 2012 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x02)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (15960) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 185) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7037)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   186   176   021    Pre-fail  Always       -       1683
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       416
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       343
 10 Spin_Retry_Count        0x0032   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       414
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       211
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       2005
194 Temperature_Celsius     0x0022   113   093   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       342         -
# 2  Extended offline    Completed without error       00%       275         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by CMXILies on 2012-01-03
I've been a Ubuntu newb for a few years now :P I must say that Maverick (10.1)has been by far the most satisfying version so far as pleasing looks, functionality, personalization, bugs and crashes. I've tried almost all of them. Good luck with 11.

---

### Post by $ixtus on 2012-01-05
it amazes me that no one else exept matt has anything to contribute with . . . :(

---

### Post by WorMzy on 2012-01-05
Well, I'm still keeping up with the topic, but I've got to admit that your problem has me just as stumped as everyone else. Usually filesystem corruption like this is caused by improper shutdowns or a failing hard disk, and as far as I can tell, neither of these is the culprit in this case.

Maybe your filesystem was created without the usual features. Post the output of the following:

```
sudo tune2fs -l /dev/sda1
```

---

### Post by $ixtus on 2012-01-07
invalid option -1
 
but -e is for error behaviour 
but when i replaced -1 with -e nothing showed exept the commands list .
 
EDIT : 
its so wierd everything works just fine... exept that nothing shows on desktop..
Is there maybe something or some button i pressed so it shows "another" clean desktop without startbar or something
 
but i can acsess my Personal Prefrence by rightclicking on desktop and change background. and than clicks to all settings

---

### Post by westie457 on 2012-01-07
Hi, run 'WorMzy' command again. This time changing the 1 for a lower-case L or just copy and paste it into the terminal.

---

### Post by $ixtus on 2012-01-07
ow sorry my bad i tough that there was  a number not letter 

here is what i got 

```
tune2fs 1.41.14 (22-Dec-2010)
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          265eeef9-bdfa-42df-897f-a36839eede48
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              38699008
Block count:              154775552
Reserved block count:     7738777
Free blocks:              145526015
Free inodes:              38456019
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      987
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Wed Dec  7 20:37:41 2011
Last mount time:          Sat Jan  7 13:06:05 2012
Last write time:          Sat Jan  7 11:19:53 2012
Mount count:              3
Maximum mount count:      27
Last checked:             Sat Jan  7 11:19:53 2012
Check interval:           15552000 (6 months)
Next check after:         Thu Jul  5 11:19:53 2012
Lifetime writes:          161 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      4df43ffc-901e-4f61-b022-1fc615b4baa0
Journal backup:           inode blocks

```

---

### Post by WorMzy on 2012-01-07
Well, that looks fine to me, so the filesystem was created correctly.

Sorry, but I have no more ideas at the present.

---

### Post by $ixtus on 2012-01-07
ok 

again like i said ... it feels that the butu is runing just fine except when i login the desktop doesnt show anything at all except the background wallpaper and the cursor 
i wonder if i pushed a something to enter another desktop or something when i was angry :(

---

### Post by WorMzy on 2012-01-07
So the boot problem has resolved itself, and you're just having configuration problems now?

That could be caused by your gconf/dconf configuration becoming corrupted, so Ubuntu falls back on the system defaults, or it could be a permissions issue.

I'd create a new topic about it, with an informative title, so that people with the right knowledge can advise you.

---

### Post by $ixtus on 2012-01-08
thank you all for help 
specially matt!

but i made my mind to go back to windows 7 unfortunately :(
i cant take this anymore , every problem that appears i can not fix by myself

---

