---
title: "TOTAL wipe of hard drive"
date: 2010-06-01
forum: General Help
---

### Post by 3948ctyj on 2010-06-01
I want to wipe the drive to the bios before shipment back to factory. I tried Daricks nuke but it wouldnt burn to usb with the usual programs.
What program will TOTALLY nuke my hard drive and work with netbootin or other UBU program..???  thanks

---

### Post by tgalati4 on 2010-06-01
Boot an Ubuntu Live CD, open a terminal:

apt-cache search wipe
sudo apt-get install wipe secure-delete
man wipe
man secure-delete

---

### Post by inameiname on 2010-06-01
Personally I use Killdisk to erase my main hard drive, as you can download and burn it for free on a floppy or a cd and run it at boot and then it'll give you the option to erase whatever drive you want. Very simple, and efficient.

Another method, if it's not your main hard drive, but say an external one, or a secondary one, is to use the 'shred' command.

 I use this for flash drives and portable hard drives all the time:

sudo shred -v -z -n 1 /dev/sdb

...where 'sdb' is whatever your drive is...

shred (insert one of the below commands) FILE (insert name of file, or  drive, or whatever) 

-f, --force
    change permissions to allow writing if necessary 
-n, --iterations=N
    Overwrite N times instead of the default (25) 
-s, --size=N
    shred this many bytes (suffixes like K, M, G accepted) 
-u, --remove
    truncate and remove file after overwriting 
-v, --verbose
    show progress 
-x, --exact
    do not round file sizes up to the next full block 
-z, --zero
    add a final overwrite with zeros to hide shredding 
-
    shred standard output 
--help
    display this help and exit 
--version
    output version information and exit

Both work great.

---

### Post by yetiman64 on 2010-06-01
> **3948ctyj said:**
> I want to wipe the drive to the bios before shipment back to factory. I tried Daricks nuke but it wouldnt burn to usb with the usual programs.
What program will TOTALLY nuke my hard drive and work with netbootin or other UBU program..???  thanks


Depending on how "sensitive" your data is, using the shred command from terminal off a live cd can completely reset a drive, For sensitive data a normal shred of /dev/sdX (where X is the drive letter eg /dev/sda) eg.
```
sudo shred --force --verbose --zero /dev/sdX
```This WILL take a long time (26 overwrites), for a simpler drive reset you could use,

```
sudo shred --force --iterations=0 --verbose --zero /dev/sdX
```This one only does a zeroing pass over the drive (resets every bit to zero) and is MUCH quicker but less "secure".

This will wipe a complete drive including MBR bootcode and partition tables etc when used on a complete drive and not just a partition. To use a drive after this is done you can install a fresh (but blank) ms-dos label using gparted (also from the live cd).

---

### Post by inameiname on 2010-06-01
Ooh, yeah, I would never use 'shred' in that manner, off a Live CD. Why an outside simple app works just fine for me, KillDisk.

---

### Post by yetiman64 on 2010-06-01
> **inameiname said:**
> Ooh, yeah, I would never use 'shred' in that manner, off a Live CD. Why an outside simple app works just fine for me, KillDisk.

@inameiname, could you tell me why it's a bad idea to do it this way?, (its a "simple" habit I've gotten into). Is it to do with the level of security or for some other technical reason or just personal preference?. Thanks in advance. yetiman64

---

### Post by inameiname on 2010-06-01
Oh no, I'm sorry. I was agreeing with you on what you wrote actually, particularly with the first part of your previous post, about 'security' and whatnot. It would take far too long to do it that way. Sorry, I should've been more clear. Rereading it, it was pretty badly written. :P Plus I was confused a little I think for a second too. Nevermind. Actually, if you noticed my previous post, I also suggested 'shred':

sudo shred -v -z -n 1 /dev/sdb

...where sdb is whatever you want..

which would erase the whole thing once over with 0s, which would wipe it entirely, just not very securely. It seems your suggestion of:

sudo shred --force --iterations=0 --verbose --zero /dev/sdX

is the exact same as mine above.

---

### Post by mkvnmtr on 2010-06-01
I would never use something I downloaded from the internet from a company that sells software when the repositories have secure-delete. 
By the way man secure-delete gets you nothing. After a secure-delete install you need to man srm.
If you have a Ubuntu live disk you can indeed use that.

---

### Post by inameiname on 2010-06-01
I hear ya. It was just another option. Though an outside source would be necessary sometimes. I mean through a live CD method, it'd have to be able to run on the computer, get online, and etc. hehe. Regardless, KillDisk was always my thing for years, to erase all, long before I ever used Linux, so guess it's stuck. hehe

---

### Post by yetiman64 on 2010-06-01
@inameiname, Understand you now :).

@3948ctyj, BTW "iterations=0" can be adjusted to any value you require security wise, though the higher it's set the longer it takes obviously.
Also just used "man shred" and noted the default has now been changed to 3 passes (used to be 25 on older releases) Cheers.

---

### Post by JustinR on 2010-06-01
I find using DD is extremely helpful.
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by Serpher on 2010-06-01
From a live disc, mount your hardrive and navigate into the directory of it and execute these commands:

```
sudo -i
rm -r *
dd if=/dev/zero of=anythingcangohere bs=1G count=999999
```

Let that run overnight and then run 'rm -r *' again.

---

### Post by 3948ctyj on 2010-06-01
I appreciate the info fellas...  I dont have a live disk...
Can I use kill disk  to wipe it anyhow??  I will be doing this 1 time on the EEE  pc  and then it will be dead...I hope....

---

### Post by yetiman64 on 2010-06-01
> **3948ctyj said:**
> I appreciate the info fellas...  I dont have a live disk...
Can I use kill disk  to wipe it anyhow??  I will be doing this 1 time on the EEE  pc  and then it will be dead...I hope....


If the EEE pc doesn't have a cd drive, the live cd iso can be written to a usb stick instead by using System > Administration > Startup Disk Creator, and the previous instructions for the live cd and shred etc used. That is, boot a live cd image from a USB stick.

I'm assuming in adding this that kill disk would need to be run from the hard drive (don't know if it can be used from boot media - anyone else know this ?) Hope this is of some use.

---

### Post by inameiname on 2010-06-02
In regards to KillDisk, it can be thrown onto a floppy, a disc, or a usb, and takes like 10mb. Really its a dos application. But as another user said, you can download the live cd too and throw it on a usb and use shred or dd or whatever, which would do the exact same thing. KillDisk is just an option that boots and runs entirely off the floppy, disc, or usb drive, just as a live cd would, that's all.

And since it sounds like all you require is a quick erase of the hard drive, 10mb download is all you need for KillDisk. Of course, if you are gonna throw on Ubuntu on a new hard drive or something, or if you already have it installed on another computer, as in the one you are using now, then the dd or shred option would probably be easiest if you have the drive hooked up to it. IDK how it is for ya.

PS, on a personal note, I can't believe I never thought about just using my Remastersys-made custom DVD, which I install on computers all the time, and use it to erase the hard drive too prior to installation. Usually I KillDisk the hard drive on the computers, and then use the live disc to install. Pretty sad I never thought about this as an option since I use 'shred' all the time for flash drives, external hard drives, just not my main hard drive. hehe

---

