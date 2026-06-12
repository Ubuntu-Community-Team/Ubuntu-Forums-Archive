---
title: "Ninja Ubuntu Laptop Vanish: How Can I Remotely Undelete?"
date: 2011-09-27
forum: General Help
---

### Post by joeyarnold on 2011-09-27
Ninja Ubuntu Laptop Vanish: How Can I Remotely Undelete?


When I had a bunch of video programs running, as my Ubuntu (operating system) HP dual-core laptop froze, I forced my computer off (via holding on the power button for around 20 seconds until it turned off).

When I turned my laptop back on, my files were gone, my preferences were gone, my operating system (Ubuntu 11.10) was gone and replaced with Ubuntu 10.04, the name of the computer was changed from Joey Arnold's computer to some random numbers and letters, the fiilesystem was different, my previous partitions were gone and replaced with new ones, and my 120 GB hard drive suddenly went from around 15 GBs of free space to around 80 GBs of free space.

I can connect my laptop to my Ubuntu desktop via an ethernet cable wire. I know how to get online from the desktop via the ethernet attached to my laptop, being that my laptop can get wireless internet. 

However, I don't know how to remotely undelete. I don't even know how to transfer files from my laptop to my desktop.

I need to restore over 80 GBs or so of data and I hear that it is better to undelete, to save, to restore, lost data onto a different hard drive. 

This seems to be my only option. 

I know how to use the terminal. Perhps there is a way to CD, to Change Directories, to go from my laptop and into my desktop via ethernet, and vice versa. Perhaps there is a program or a command that allows for the option for where u want to restore a undeleted file to, because I see that there are options for what folders you want to restore lost data to, so why not restore to a folder in a different computer connected via ethernet or wireless?

---

### Post by ajgreeny on 2011-09-27
If you can boot to a live Ubuntu CD it would be useful if you use the command ```
sudo fdisk -l
``` and report the output back here.  That will tell us what partitions are on your hard disk.

I find it hard to believe that a hard reset would erase all your files and operating system, though it can occasionally make it impossible to boot the machine.  However, I presume your comments about partition sizes means you have already looked with a live system of some sort.

More information please about exactly what happened and what you have already done to find out what you've said here.

---

### Post by joeyarnold on 2011-09-28
> **ajgreeny said:**
> If you can boot to a live Ubuntu CD it would be useful if you use the command ```
sudo fdisk -l
``` and report the output back here.  That will tell us what partitions are on your hard disk.

I find it hard to believe that a hard reset would erase all your files and operating system, though it can occasionally make it impossible to boot the machine.  However, I presume your comments about partition sizes means you have already looked with a live system of some sort.

More information please about exactly what happened and what you have already done to find out what you've said here.
[SIZE=4][COLOR=Red][B]


Do I have to boot from a live Ubuntu CD in order to type in that code in the terminal (Sudo Fdisk -L) in order to get the most accurate results or output or answers? [/B][/COLOR][/SIZE]

Like I already said, I lost all of my data and my operating system reverted from Ubuntu 11.10 to 10.04. But since I can still boot up, I typed in sudo fdisk -l in the terminal and got the following output:


[SIZE=4][COLOR=Red][B]
Laptop Input:[/B][/COLOR][/SIZE]

On my Ubuntu 10.04 broken Lost-Data Laptop, I typed in:

```
sudo fdisk -l
```[SIZE=4][COLOR=Red][B]


Laptop Output:[/B][/COLOR][/SIZE]

```
o@o-HP-Compaq-6910p-GH715AW-ABA:~$ sudo fdisk -l
[sudo] password for o: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca236

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14411   115755008   83  Linux
/dev/sda2           14412       14594     1463297    5  Extended
/dev/sda5           14412       14594     1463296   82  Linux swap / Solaris

```

---

### Post by ajgreeny on 2011-09-28
Sorry I am a bit confused.  After loosing all your files and folders it looks as if you did a new clean install of 10.04 in place of your old 11.04, or do you mean that happened with no input from you, and that you have not installed a new system?

Whatever your answer i think your best hope, though the chance may be low if you have continued to use the machine, is to install testdisk on a live CD of ubuntu and try using that to recover your old files and folders.  This is not something I have ever done but I understand it can be successful from others who have used it.

The more you use the machine that has had this problem the more likely you are to completely lose the files from it, hence my suggestion of using a live CD.

---

### Post by joeyarnold on 2011-09-28
> **ajgreeny said:**
> Sorry I am a bit confused.  After loosing all your files and folders it looks as if you did a new clean install of 10.04 in place of your old 11.04, or do you mean that happened with no input from you, and that you have not installed a new system?

Whatever your answer i think your best hope, though the chance may be low if you have continued to use the machine, is to install testdisk on a live CD of ubuntu and try using that to recover your old files and folders.  This is not something I have ever done but I understand it can be successful from others who have used it.

The more you use the machine that has had this problem the more likely you are to completely lose the files from it, hence my suggestion of using a live CD.


[COLOR=Red][B]
Yes. Correct. My laptop reset itself. [/B][/COLOR]

I bought this laptop at Free Geek ([http://FreeGeek.org](http://FreeGeek.org)) and I also posted this thread on the Linux Questions forum, too ([http://www.linuxquestions.org/questions/showthread.php?p=4484522&posted=1#post4484522](http://www.linuxquestions.org/questions/showthread.php?p=4484522&posted=1#post4484522)). This thread is also posted here, too ([http://ubuntuforums.org/showthread.php?p=11294238#post11294238](http://ubuntuforums.org/showthread.php?p=11294238#post11294238)). Plus, this thread was also posted here, too ([http://ubuntuforums.org/showthread.php?p=11267372#post11267372](http://ubuntuforums.org/showthread.php?p=11267372#post11267372)).


[COLOR=Red][B]
Free Geek said that the OEM-Config script thing[/B][/COLOR].....

......probably got corrupted or activated or something, which can cause a flush, a reset, which restores the computer to a default state with just the basics of the original operating system (Ubuntu 10.04) before I ended up updating or upgrading the OS up to Ubuntu 11.10. It may cost me money to get it fixed. But I have no money, job, life.
[COLOR=Red][B]

I have used Test Disk, and other programs before.[/B][/COLOR]

I might have it on my computer right now. If not, I know how to get it. I want to know about other programs. 

[B][COLOR=Red]
I need code or a way to restore my data onto my desktop via ethernet.[/COLOR][/B]

[COLOR=Red]**Does anybody have a live Ubuntu CD they can send me? **[/COLOR]

I might have one. But I can't access wifi internet via a live Ubuntu CD currently. There are ways but it is tough to get online with my wireless device because the live CD has to be able to recognize my wireless device in order to allow it to connect to wifi internet.
[B]
In other words, while I am on a live CD, I am on my own, and I just need a plan before going off on my own.

Because I don't know how to transfer files from my laptop to my desktop via ethernet.
[COLOR=Red]




Main Question:

How can I transfer files from my laptop to my desktop via ethernet?[/COLOR]

?
[/B]

---

### Post by joeyarnold on 2011-09-28
> **ajgreeny said:**
> Sorry I am a bit confused.  After loosing all your files and folders it looks as if you did a new clean install of 10.04 in place of your old 11.04, or do you mean that happened with no input from you, and that you have not installed a new system?

Whatever your answer i think your best hope, though the chance may be low if you have continued to use the machine, is to install testdisk on a live CD of ubuntu and try using that to recover your old files and folders.  This is not something I have ever done but I understand it can be successful from others who have used it.

The more you use the machine that has had this problem the more likely you are to completely lose the files from it, hence my suggestion of using a live CD.



Here's what probably happened:

[COLOR=Red]**OEM Config Error = Laptop Reset = Automatic New Clean Install of Ubuntu 10.04:**[/COLOR]


[Free Geek]("http://freegeek.org") (where I bought this laptop from) says:

.....That an OEM-Config script error or malfunction or problem or activation causes an automatic new clean install of Ubuntu 10.04. In other words, this OEM-Config script causes a reset, a flush, returning the whole entire laptop back to default settings, erasing everything, and returning everything back to defaults, default settings, defaults ways, to make it look like a brand new computer that was never ever used at all. 

Sorry, I know I already said this already in my last post. I just wanted to resay it again for clarity.

---

### Post by joeyarnold on 2011-09-28
OEM-Config reset my laptop. How can I undelete everything from my laptop to my desktop via ethernet?

---

### Post by joeyarnold on 2011-09-29
should I use Net Cat to undelete my lost laptop files and have them recovered onto my desktop tower computer via ethernet wire?

If so, how do I find Net Cat? Which version works best for Ubuntu 10.04?  Where do I download it from? Are there different Net Cat programs?   Which one should I use exactly?

---

### Post by joeyarnold on 2011-09-29
[http://www.ubuntu.com/](http://www.ubuntu.com/). 

They use to mail people CDs for free. Now it cost like a dollar. 

I found some of my CDs but I don't know if they are specifically the live CDs or not. 

Does it matter if it says live on it or not? I have this CD that does  not say live on it but it does say Ubuntu 10.04 LTS Desktop Edition. 

I have used it before It can install Ubuntu 10.04 onto most computers.  There is also the option of trying it out before installing it. 

Meaning that you can boot onto the CD. So, is that the same as a live CD  then? If so, then I should be able to get onto this live Ubuntu 10.04  CD then. 

But I can't get online from a live CD yet because my wireless internet  device stops working during a live Ubuntu CD session. That is why I want  a plan before going live.

One CD says G Parted Ed 0.4.6. Can this CD help with anything?

---

### Post by joeyarnold on 2011-09-29
i still need help

---

### Post by cryptotheslow on 2011-09-29
Yes that &quot;Ubuntu 10.04 LTS Desktop Edition&quot; will do fine. Just choose the &quot;Try Ubuntu&quot; button once you get to the desktop.  How much space do you have on the hard-disk of your desktop machine?  I ask as it would probably be preferable (if you can physically connect your laptop drive to the desktop machine), to take a complete copy of the laptop drive using the dd command. And then you can try your file recovery techniques on the copied image file rather than accessing the hard drive itself.  Ideally you would plug the laptop drive into the desktop, use dd to make an image of the drive in a file on the desktop, then make a copy of that image file on the desktop - giving you two copies of the data to work on - just in case your file recovery procedures somehow corrupt the images.   EDIT - Don't ask me what happened to the format and paragraph in this post! Very weird behaviour using Firefox 7!

---

### Post by fixerdave on 2011-09-29
Not sure of all the restrictions you're working under here...

Let see if I've got this right:
* You have a desktop and a laptop.  
* The laptop has basically been reformatted to an earlier version of Ubuntu through some recovery script.
* You want to recover the files on the laptop by copying them to your desktop over Ethernet.
* You have limited internet access... maybe only wireless via your laptop, and you can't get wireless via liveCD.

I'd say the easiest way to move files between your laptop and desktop is to create a share on your desktop and then map it from the laptop.

As others have said... if you're trying for data recovery, the less you use the laptop drive the better.  Best to use a liveCD for the recovery attempts.  Also, again already said, the first step in any recovery should be to make a byte-for-byte snapshot of the damaged drive.  

The program ddrescue will make a snapshot for you.  After that, there are a lot of options and you can keep trying them, one after the other BECAUSE you have the snapshot you can use to reset everything between attempts.  If your first attempt basically wipes everything off the disk... so what?  You just put your snapshot back on the disk and try the next thing.

Honestly, if I were in your position, I would get a wireless card for my desktop - they're cheap and it will give you internet access when you need it.  It will make the rest a lot easier.

A long time ago, I wrote a blurb on data recovery here:
[http://datadave.blogspot.com/2008/08/data-recovery-with-ubuntu-linux-live-cd.html](http://datadave.blogspot.com/2008/08/data-recovery-with-ubuntu-linux-live-cd.html)

There are probably better ones out there but it might help get you started.

---

### Post by collisionystm on 2011-09-29
@OP dude that Has happened to me 3 times. I just keep all my **** on a USB hard drive

---

