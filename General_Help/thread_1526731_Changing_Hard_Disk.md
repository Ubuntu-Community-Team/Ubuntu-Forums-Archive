---
title: "Changing Hard Disk"
date: 2010-07-08
forum: General Help
---

### Post by JCM_Pico on 2010-07-08
hello there,
I have a laptop running Ubuntu (only), and now I got a new hard disk.
And I would like to copy the entire installation to the new bigger and faster disk, without having to compile and install all the software I got on it. And also I would like to create a  partition for installing windows for playing since playing in a emulator its kind of slow...
I've read some ways of doing it but  it brought some doubts.
The first is to use Remastersys, can I do a this, pass it to a external USB disk and just install it ?
The second  is to use Partimage, this seem to be the easiest way of doing it.

Is there anybody how already have done this who could give me some advice 

thank you all

---

### Post by colorlessprism on 2010-07-08
if you want to go the easiest route, i think remastersys would work well for you, however you should install windows first. if you install Ubuntu and then windows i doubt you will be able to get back to Ubuntu. i do not know what partition editors are available in the version of windows you plan to use. i would make a remastersys image. when your ready to commit boot (from CD/USB) to your custom liveCD and run gparted (or equivalent) and partition your hdd as desired. then install windows to the partition you want, then install ubuntu (from your remastersys backup) and if all goes well you will have a dual boot system

Here is a Remastersys guide I created:
[http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

---

### Post by JCM_Pico on 2010-07-08
I'm attending to install windows 7 or XP, but I was wondering if I could do it some time after changing the hard drive ... So isn't really recommended do install a windows partition after having ubuntu running in half of the disk space. 
By the way thank you for the advice and help :)

---

### Post by lmarmisa on 2010-07-08
Try to use Clonezilla:

[http://clonezilla.org/](http://clonezilla.org/)

It works great.

---

### Post by spiky001 on 2010-07-08
It is best to load windows 1st as mentioned above, or when you load win after ubuntu grub gets over written by windows mbr then a bit of work is required to fix it but it can be done

---

### Post by ezsit on 2010-07-08
I would second the suggestion to use remastersys **if** your entire system can be backed up and fit on a single DVD (4.3 GiB or less). If your system cannot be backed up onto a single DVD, then I would backup your /home folder to USB stick and still use remastersys to create a DIST mode backup of your system. You can always restore the /home folder contents after reinstallation (and use the exact same username when you reinstall).

---

### Post by JCM_Pico on 2010-07-08
clonezilla needs to have the 2 disks running in the same machine, a thing that I can't do... Thank you for the help even so

I will use the Remastersys thank you all for the help. If I have any trouble I'll post again :)

---

### Post by lmarmisa on 2010-07-08
Clonezilla is able to backup in an smart way all the content of your hard drive (or partions) in an external USB drive (backup). Then , you can restore the backup in your new hard drive. Clonezilla does not need both disks running in the same machine.

If you wish to define new partitions for Windows or other purposes, use GParted.

Kind regards,

Luis

---

### Post by JCM_Pico on 2010-07-08
thank you Luís
I already started to backup, but if I find any difficulty I'll try clonezilla

obrigado

---

### Post by JCM_Pico on 2010-07-08
well I've tried to make the backup with Remastersys but it failed, because the file was too large to use ISO. Now I have a huge folder called remastersys in my home folder... can I delete it?
Is there a way to avoid the file size problem

---

### Post by lmarmisa on 2010-07-08
Try Places -> Search for files... Look in folder / & Select more options: Size at least and select a size of 500 Mbytes or something like that.

---

### Post by JCM_Pico on 2010-07-08
I have backup of my personal file, that I made using rsync...
I will try to make a installation backup using remastersys with the dist option
will this completely make my new disk with the same installation than the old one ?

---

### Post by colorlessprism on 2010-07-08
try following the guide. you probably have a lot of "Media" files (music, pictures, videos, etc) you will want to comment those out in the remastersys options and back them up separately. 

you can open the remastersys program and on the menu there is a "clean" option and this will remove the failed backup. or (as my preference) open a terminal and type :
sudo remastersys clean

---

### Post by JCM_Pico on 2010-07-08
Hi there again, I'm having some trouble to install the installation... I have created a start-up disk using the startup-disk creator, from the remastersys.iso. But it seams to does not work very well.. the hole folder occupy 7.2 Gb and the ISO only give me 3.5 Gb... is this normal

---

### Post by JCM_Pico on 2010-07-08
With remastersys, the copy of my installation was unsuccessful. I would like to keep all my definitions, and to make that I need to do a full back up, and that is impossible with ISO

I already took a look at clonezilla but it seams a bit difficult to make it run from a bootable USB hard drive 
Any help on this

---

### Post by lmarmisa on 2010-07-08
Clonezilla boots up from a CD or from a pen drive.

---

### Post by colorlessprism on 2010-07-08
the only way you will be able to use remastersys in the way you want would be to comment out your media folders. once done back your media up to something and go for it.

---

### Post by JCM_Pico on 2010-07-08
I'm giving a try to partimage... let's see what come out

---

### Post by JCM_Pico on 2010-07-09
Well I made it sucessefuly with partimage, but now I got plenty of disk space (329Gb) but I keep only with 100Gb in my system (using df -l command)...
Who can I get the hole disk space.
I know that with remastersys this problem would be avoid... but I really want to keep all my sys. configuration, and I wasn't able to do this when I try to use remastersys.
Any help

---

### Post by JCM_Pico on 2010-07-09
> **colorlessprism said:**
> the only way you will be able to use remastersys in the way you want would be to comment out your media folders. once done back your media up to something and go for it.

how can I comment my media
does remastersys copy the hidden files too

---

