---
title: "Help - grub has hijacked my computer."
date: 2012-01-08
forum: General Help
---

### Post by Mightyq12 on 2012-01-08
It may sound dramatic, but it's the most appropriate way I have to describe what happened.  I built my computer, and installed Windows 7 on a 1TB hard drive.  I then wanted to learn about Ubunut, so I got a smaller hard drive, and installed Ubuntu on that one, and had them both running concurrently.  The problem is, ever since then, the second hard drive isn't doing anything correctly.  

I don't use Ubuntu as much anymore, and when I'm IN Windows 7, the computer doesn't register the drive as a possible storage device.  It just isn't in the directory of drives, at all.  Furthermore, when I remove the drive, and attempt to boot up with just the primary Windows 7 drive, the computer will not start at all, and just say that there is a missing file, and the computer can not even enter BIOS.  This is a serious problem, and I feel like it jeopardizes the overall integrity of my computer.  Does anyone know how I can fix this, and just wipe the hard drive, and use it for storage?

---

### Post by wolfen69 on 2012-01-08
> **Mightyq12 said:**
> when I'm IN Windows 7, the computer doesn't register the drive as a possible storage device.  
This is because windows does not have the capability to see linux partitions.

> It just isn't in the directory of drives, at all.  Furthermore, when I remove the drive, and attempt to boot up with just the primary Windows 7 drive, the computer will not start at all 
You need to insert your win7 cd and choose the boot repair option.
> 
the computer can not even enter BIOS.
Ubuntu does not tamper with bios's. The bios always loads *before* ubuntu, so you need to look at other possible reasons for this.

Once you fix your windows boot sector, just get into windows and format the ubuntu drive to NTFS. Good luck.

---

### Post by bluexrider on 2012-01-08
If you want to dual boot the PC I recommend reading this

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Double.J on 2012-01-08
+1 to Wolfen69 and BlueXrider, to be honest I had to read this thread for the title!

But yest just adding to that - it seems that you want Ubuntu gone, if you changed your mind, or wanted to try another open source OS in the future, I'd advise installing the bootloader to the main partition you install the OS - in an ubuntu installation you have to choose "something else" for this.

Then install [easyBCD]("http://neosmart.net/EasyBCD/") in windows, tell it where ubuntu is and you should have an easy to boot, easy to put right system - if you delete ubuntu windows 7 would still boot and you could change the menu entry so easy bcd boots automaticaly as if it weren't there.

sorry you've had unexpected issues with it, I hope you stick with Ubuntu :)

---

### Post by Mightyq12 on 2012-01-08
At this point, I'm not really concerned with keeping Ubuntu, it's just given me a little too much trouble.  I've never been very good at messing around in BIOS - I was wondering if anyone had a little more... Guided?  advice on how to fix it?  I don't have the Win 7 CD, and was hoping to just reformat the Ubuntu drive, but I'm concerned that if I do, the system will still look for the grub file, and then I'll be stuck in a startup-less limbo.

---

### Post by Double.J on 2012-01-08
> **Mightyq12 said:**
> At this point, I'm not really concerned with keeping Ubuntu, it's just given me a little too much trouble.  I've never been very good at messing around in BIOS - I was wondering if anyone had a little more... Guided?  advice on how to fix it?  I don't have the Win 7 CD, and was hoping to just reformat the Ubuntu drive, but I'm concerned that if I do, the system will still look for the grub file, and then I'll be stuck in a startup-less limbo.

Make a windows7 back up - choose full hdd image (you should always back up before doing anything HDD anyway) it'll ask you if you want to make a recovery cd... you do - this way you have a bckup before you do anything (yay!) and a start up disk (more yay!)

Disconect the windows disk, and use the ubuntu installation media you used to boot the pc - select try. then go to the launcher and type 
> 
gparted

start gparted.
you now have to _CHECK_ that the hard drive table shown is the ubuntu one - does it have ext4 partition (s) - if yes good. Does it have NTFS partitions? - if yes, STOP! check again that this is not your windows disk.

If it passes this check, delete all the partitions on it and click apply. then new> type primary, ntfs, apply and turn off the PC.

Reconnect your windows HDD and restart from the disk you made - choose repair options and fix start up issues or similar - this may need to be run more than once ;)

all the best :)

---

### Post by Mightyq12 on 2012-01-09
And if I don't have/remember which Ubuntu install media I used?

---

### Post by Double.J on 2012-01-09
> **Mightyq12 said:**
> And if I don't have/remember which Ubuntu install media I used?

Not a problem! this can be done from any live cd! You can even get one that is just the gparted program I mentioned! - [gpartedlivecd]("http://gparted.sourceforge.net/download.php")

---

### Post by Mightyq12 on 2012-01-09
Honestly, based solely on how helpful you are, I'm considering making Ubuntu my primary OS on my 1TB drive, to eliminate all future problems like this, and become more acquainted with Ubuntu.  Do you also have any pointers on making Ubuntu LOOK more... Windows-like?  It's hard to describe, but Ubuntu is kind of... New-Agey, I guess, I just happen to prefer the overall look of Win 7.

---

### Post by carl4926 on 2012-01-09
Hang on
One minute you are wanting to get rid of Linux and now you want to get rid of windows...

But you want Ubuntu to look more like Windows

If you used kubuntu, you might find that easier to do

But I think you need to do some careful thinking. It puzzles me that your comments suggested you were in possession of a Windows DVD>  I built my computer, and installed Windows 7 on a 1TB hard drive
And yet you say you don't have a Win7 DVD

From what I read
You probably wrote the Grub to the MBR of sda, which will mean you need a Windows DVD or similar to repair the MBR if you plan to delete Ubuntu.

Of course you could dump windows and install Ubuntu or Kubuntu to the 1TB hd
But I would partition it manually first and set aside some store space too.

---

### Post by Double.J on 2012-01-09
> **Mightyq12 said:**
> Honestly, based solely on how helpful you are, I'm considering making Ubuntu my primary OS on my 1TB drive, to eliminate all future problems like this, and become more acquainted with Ubuntu.  Do you also have any pointers on making Ubuntu LOOK more... Windows-like?  It's hard to describe, but Ubuntu is kind of... New-Agey, I guess, I just happen to prefer the overall look of Win 7.

I don't blame you - it's a mighty fine looking OS. If you don't like unity, there are other esktop environments to check out. KDE and LXDE come to mind here's what they look like with their menus open
KDE
[IMG]http://imag.malavida.com/mvimgbig/download/kubuntu-5920-1.jpg[/IMG]

LXDE
[IMG]http://www.visualbeta.es/files/2011/07/lubuntu1110.jpg[/IMG]

If you wanted to to give them a try KDE has more visual effects, LXDE is designed to use less resources - but it's really not naff! just be warned adding them does add extra programs that they use - terminals, texts editors - this annoys some people... if you're likely to get annoyed by this don't do it, but if you want to give either or both a go

```

sudo apt-get install kubuntu-desktop

```
for KDE or for LXDE
```

sudo apt-get install lubuntu-desktop

```

you change between them by signing out and selecting them from the cog next to the sign in box

Hope it helps!

---

### Post by duncan12 on 2012-01-09
> **Mightyq12 said:**
> Do you also have any pointers on making Ubuntu LOOK more... Windows-like?  It's hard to describe, but Ubuntu is kind of... New-Agey, I guess, I just happen to prefer the overall look of Win 7.

Ubuntu is highly themable. For a Windows 7 theme you might want to look at [this]("http://my.opera.com/ubuntunerd1/blog/how-to-make-ubuntu-look-like-windows7"). Haven't tried it but seems good. Other than that you can look at [this GNOME website]("http://art.gnome.org/themes") for more themes and personalisation.

HTH

---

### Post by Mightyq12 on 2012-01-09
Let me explain;
It's not that I explicitly want to get rid of Ubuntu, it's that currently, I need that hard drive for storage space, and because Windows can't see the partition, I can't move files onto it.

I understand and appreciate the appeal of an open-source software like Ubuntu, but I have used Windows my whole life, and have come to really like it.  That, and I enjoy gaming, and am not sure how my games would fare in a virtual machine.

---

### Post by Double.J on 2012-01-09
> **Mightyq12 said:**
> Let me explain;
It's not that I explicitly want to get rid of Ubuntu, it's that currently, I need that hard drive for storage space, and because Windows can't see the partition, I can't move files onto it.

I understand and appreciate the appeal of an open-source software like Ubuntu, but I have used Windows my whole life, and have come to really like it.  That, and I enjoy gaming, and am not sure how my games would fare in a virtual machine.

You could use the live cd i mentioned to reduce the size for ubuntu to as low as 15gb and have the rest of the drive as ntfs for windows?

---

### Post by carl4926 on 2012-01-09
Sounds like you need to keep windows to me

You need to perhaps show us your partitioning
Open a terminal in Ubuntu and do

```
sudo fdisk -l
```

Post the result here

We may be able to make a suggestion
But as I said earlier, it's looking like you need to get hold of a Win7 DVD or
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Fix windows and format the ubuntu hd to use as storage

---

### Post by mastablasta on 2012-01-09
> **Mightyq12 said:**
> Let me explain;
It's not that I explicitly want to get rid of Ubuntu, it's that currently, I need that hard drive for storage space, and because Windows can't see the partition, I can't move files onto it.
 
I understand and appreciate the appeal of an open-source software like Ubuntu, but I have used Windows my whole life, and have come to really like it. That, and I enjoy gaming, and am not sure how my games would fare in a virtual machine.
 
if you are using it for storage space only then you do not need to fix the master boot record (grub) that is only needed to install windows to it. to see the disk you need to reformat it in NTFS file system. you can use gparted for that or windows install CD will also do it.
 
if however you want to stick windows on this 1TB disk then you need to repair/replace the master boot record first
 
otherwise windows can see the ext3/ext4 file system that linux uses by default on install, however you need some plugins to do that and perahps a more advanced file manager than windows explorer.
 
 
it is possible to use both systems on same hard disk. linux needs abotu 25-30 GB for system and some of your files. you can use windows part of disk for data storage and such. and also gaming. not many new games work in linux as they are windows based.
 
most windows look and behaviour is found in KDE (Kubuntu) environment. i am not talking just about start button here, but also the control panel, the way system settings are done and presented in GUI etc. for old style widnows like menu you need to right click the K in KDE and select classic menu style.

---

