---
title: "My hardrive is dead will ubuntu CD still be able to recover my data!?"
date: 2010-06-09
forum: General Help
---

### Post by butterfliez321 on 2010-06-09
I can't lose all my data i have 3 years worth of pictures , documents , music T_T.
Ok..so i have ubuntu running on now and i think my hardrive is broken/dead now becuase i tried doing the trick of putting it in the freezer and now my computer is saying cannot find hardrive error blah blah..
 
So last time i tried ubuntu when my hardrive was half broken i guess and i kept getting mount errors when i tried to access my C drive. it said stuff like run chkdsk somthing like that. idunno what commands to do either someone please help thank you very much!!!!

---

### Post by TheStroj on 2010-06-09
Don't worry, nothing is lost.

You can put in a Ubuntu Live CD and run it without touching disk (that's what the Live CD does - runs from CD). 
When you get to the desktop, mount disk, simply 'open' it and copy the files to some other device (like USB stick). From Live CD you can do this on the same way as when installed.

---

### Post by butterfliez321 on 2010-06-09
Hmm..im kinda confused am i supposed to see the c drive anywere? - thats were all my stuff is saved. 

im not sure how to get to my stuff and then save it sorry im noob :( XD.

---

### Post by 98cwitr on 2010-06-09
> **butterfliez321 said:**
> Hmm..im kinda confused am i supposed to see the c drive anywere? - thats were all my stuff is saved. 

im not sure how to get to my stuff and then save it sorry im noob :( XD.

there are no drive path letters in Linux as in Windows. If it's already mounted, you'll see the icon on the desktop. If not:

Find the Disk Utility under the administration menu and mount the drive from there, it will then show up on your desktop if it mounts correctly.

if not try

```
sudo mount /dev/sda1 /mnt
```

where /dev/sda1 is the slaved drive (disk utility will tell you this also.

If you're still having trouble understanding, I can post screenshots when I get home.

---

### Post by TheStroj on 2010-06-09
If you know how to run a Live CD sesion, nothing else is a problem ;).

Put in a CD from which you installed Ubuntu and when it comes to the menu tell it to load without touching disk (that would be it).

You will get to a desktop, same as when you do a fresh install. Now open 'My computer' (Places - My computer) and double-click the icon that represents what you need (in my case, windows partition is listed as '73 GB ....'. 
When you open it, you'll see Windows files :). Now just copy files from there to somewhere where you want them (portable disk, USB stick, maybe the internet).

---

### Post by bodhi.zazen on 2010-06-09
Hard to know. If your hard drive is not functioning you may or may not be able to recover your data.

Boot a live CD and try to fix your file system

```
sudo fsck /dev/sda1
```

Change "/dev/sda1" to your actual partitions to recover.

If that fails, try testdisk. testdisk is in the repos

```
sudo apt-get install testdisk
```

If test dis fails try photorec (photorec is part of the test disk package, so it should have installed when you installed test disk).

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)

If photrec fails you may need professional assistance.

In the future, if the data is important to you, you need back ups on external media. Mission critical data is kept on external media off site.

Don't feel too bad, many of us have learned this lesson the hard way.

---

### Post by butterfliez321 on 2010-06-09
ok i went to the disk utility but i cannot find my hardrive in there or the C drive and stuff but i see stuff like pictures , music , documents and they are all empty

---

### Post by butterfliez321 on 2010-06-09
> **TheStroj said:**
> If you know how to run a Live CD sesion, nothing else is a problem ;).
 
Put in a CD from which you installed Ubuntu and when it comes to the menu tell it to load without touching disk (that would be it).
 
You will get to a desktop, same as when you do a fresh install. Now open 'My computer' (Places - My computer) and double-click the icon that represents what you need (in my case, windows partition is listed as '73 GB ....'. 
When you open it, you'll see Windows files :). Now just copy files from there to somewhere where you want them (portable disk, USB stick, maybe the internet).
 ok so i think im at the menu ..when it says try ubuntu 10.04 without making changes to the system and stuff am i supposed to pick the one where it says "install ubuntu 10.04" is that the live CD? :) becuz ive been picking the one that says "try ubuntu 10.04 lol

---

### Post by ajgreeny on 2010-06-09
Did you install this ubuntu OS on separate partitions or from within your windows OS?  I am just wondering if this is a WUBI install, meaning it runs rather like any other windows application, and will need windows running properly to get  itself up and running.  Also bear in mind that if the disk really and truly is "dead", and can not be read in any way, that you may have lost all your files

The "try ubuntu without changing your hard disks" is the correct way to run the live CD.  You will then need to go to the places menu and find the partition which is your ubuntu. Double clicking on that will mount it and open it in nautilus and you can then navigate to /home/*username* and see if your files are there.  If they are, make sure you back them up onto an external usb drive or something similar before you try anything else.  If you see the folders as you said you can, you should be able to see files within them, unless, of course you were looking at the folders of the live CD itself, which will always be empty.

If you did install with wubi, all this will not work that way, I'm afraid, and you will need someone else to tell you the details of how to retrieve your files, as I'm afraid I have absolutely no idea.

---

### Post by butterfliez321 on 2010-06-09
> **ajgreeny said:**
> Did you install this ubuntu OS on separate partitions or from within your windows OS? I am just wondering if this is a WUBI install, meaning it runs rather like any other windows application, and will need windows running properly to get itself up and running. Also bear in mind that if the disk really and truly is "dead", and can not be read in any way, that you may have lost all your files
 
The "try ubuntu without changing your hard disks" is the correct way to run the live CD. You will then need to go to the places menu and find the partition which is your ubuntu. Double clicking on that will mount it and open it in nautilus and you can then navigate to /home/*username* and see if your files are there. If they are, make sure you back them up onto an external usb drive or something similar before you try anything else. If you see the folders as you said you can, you should be able to see files within them, unless, of course you were looking at the folders of the live CD itself, which will always be empty.
 
If you did install with wubi, all this will not work that way, I'm afraid, and you will need someone else to tell you the details of how to retrieve your files, as I'm afraid I have absolutely no idea.
 ok umm I installed ubuntu and then burned it on a CD from my brothers computer and put the CD in my computer .

 And well my harddrive was working before but then i got these mounting errors on ubuntu so i thought my hardrive was broken so i put it in the freezer overnight and i guess it killed it ><

---

### Post by 98cwitr on 2010-06-09
> **butterfliez321 said:**
> ok so i think im at the menu ..when it says try ubuntu 10.04 without making changes to the system and stuff am i supposed to pick the one where it says "install ubuntu 10.04" is that the live CD? :) becuz ive been picking the one that says "try ubuntu 10.04 lol

DO NOT CHOOSE 'INSTALL UBUNTU...' unless you want to lose all your data.....
those folders are NOT your drive, they are on the CD. Again, you will see the mounted HD on the DESKTOP. You need to mount the drive, it the drive will not mount, please post the errors. Once you get the filesystem mounted all you have to do is plug in an external usb drive and just copypasta your data over.

---

### Post by butterfliez321 on 2010-06-09
> **98cwitr said:**
> DO NOT CHOOSE 'INSTALL UBUNTU...' unless you want to lose all your data.....
those folders are NOT your drive, they are on the CD. Again, you will see the mounted HD on the DESKTOP. You need to mount the drive, it the drive will not mount, please post the errors. Once you get the filesystem mounted all you have to do is plug in an external usb drive and just copypasta your data over.
ok i did not choose install ubuntu but i almost did. Thx D:
So heres whats what : On the desktop the only thing i see is...EXAMPLES and Install ubuntu 10.04 
 
So i went to the disk utility like you said before and heres what i see :
 
**Local Storage**
 
**PATA Host adapter **
82801G (ICH7family) IDE Controller
 
**Peripheral Devices**
USB,firewire
 
**704 MB file   <---** would this be it? it said it is mounted but my hardrive has more space than this.
Filesystem, squashfs
 
**Generic Compact flash **
 
**Generic SM/xD - picture **
 
**Generic SD/MMC**
[B]Generic MS/MS Pro
[/B]
 
Im not exactly really sure if my hardrive is truly 'dead' but when i start up windows it says cannot find or read hardrive :( 
 
should i freeze my hardrive overnight again and then run ubuntu to see if this works?

---

### Post by bodhi.zazen on 2010-06-09
From the live CD, show us the output of this command :

```
sudo fdisk -l
```

---

### Post by butterfliez321 on 2010-06-09
> **bodhi.zazen said:**
> From the live CD, show us the output of this command :
 
```
sudo fdisk -l
```
 ok sorry for being so noob but where exaclty do i put this code in XD?

---

### Post by bodhi.zazen on 2010-06-09
LOL

From your menu, open a terminal and enter the command.

---

### Post by bodhi.zazen on 2010-06-09
Oh, and you can copy and paste the output easily.

In the terminal, use the mouse to highlight the text you wish to  paste here.

move the mouse to your forums post and press the mouse wheel down.

Or use the copy - paste options on the menu in terminal and firefox.

---

### Post by butterfliez321 on 2010-06-09
> **bodhi.zazen said:**
> Oh, and you can copy and paste the output easily.

In the terminal, use the mouse to highlight the text you wish to  paste here.

move the mouse to your forums post and press the mouse wheel down.

Or use the copy - paste options on the menu in terminal and firefox.
ok so i put in that code and im not getting anything

---

### Post by linuxman94 on 2010-06-09
Make sure that it is an 'l' not a '1'. Just copy and paste the code.

```
sudo fdisk -l
```

---

### Post by bodhi.zazen on 2010-06-09
> **butterfliez321 said:**
> ok so i put in that code and im not getting anything

If that command does not give you any output = game over, sorry.

I would confirm the command is correct, but if it were not you would get an error message.

If you would copy-past the output we can review it for you and confirm or modify the code.

---

### Post by butterfliez321 on 2010-06-09
ok im really not getting anything and I put the code in right T_T but...isn't there anything else i can do...? I really don't wanna give up T_T. I've been trying for 5 days now

---

### Post by bodhi.zazen on 2010-06-09
> **butterfliez321 said:**
> ok im really not getting anything and I put the code in right T_T but...isn't there anything else i can do...? I really don't wanna give up T_T. I've been trying for 5 days now

At this point, from what you are describing, you are entering into the realm of a professional data recovery service and even then you may not have partial data recovery at best.

---

### Post by butterfliez321 on 2010-06-09
-Sighh- ok...i really appreciate everyone helping me thx~

---

