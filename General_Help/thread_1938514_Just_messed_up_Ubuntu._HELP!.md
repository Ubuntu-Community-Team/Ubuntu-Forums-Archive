---
title: "Just messed up Ubuntu. HELP!"
date: 2012-03-09
forum: General Help
---

### Post by louisgonick on 2012-03-09
Less than an hour ago, my system was running perfectly. I wanted to install some icons I had downloaded but just drag and drop wouldint work. I couldn't recall what do to to be able to drag the icons into usr/share/icons. I tried a few commands I found online, I used this one:
```
sudo rm -r /usr/share/icons/
```

After that all my icons were blank, I tried rebooting and Ubuntu froze just after boot up. Its impossible to use it now. 

Some people are starting to tell me to re-install Ubuntu, this will result in the loss of ALL my files, and this makes me panic. I had some VERY important documents in Ubuntu. 

In the case I re-install, is there any way that I could recuperate all of my files? 
I NEED HELP!

---

### Post by winh8r on 2012-03-09
Use a LIVE CD to access your hard drive and remove all important files before you do anything else.


Email the documents to your email address, you can usually send emails to yourself in most accounts.

---

### Post by coldraven on 2012-03-09
Don't panic! Just boot up with a live CD and copy all your important stuff to an external drive or memory stick. Then ask someone with a dropbox account to zip a copy of /usr/share/icons and let you download it. I just checked and you have deleted 115MB of icons!

---

### Post by louisgonick on 2012-03-09
> **coldraven said:**
> Don't panic! Just boot up with a live CD and copy all your important stuff to an external drive or memory stick. Then ask someone with a dropbox account to zip a copy of /usr/share/icons and let you download it. I just checked and you have deleted 115MB of icons!

> **winh8r said:**
> Use a LIVE CD to access your hard drive and remove all important files before you do anything else.


Email the documents to your email address, you can usually send emails to yourself in most accounts.

Thanks, I am in the process of burning ubuntu to a CD now. I will post updates

---

### Post by coldraven on 2012-03-09
I just compressed the contents of /usr/share/icons and am try to upload it to Ubuntu One.
I have never used it before so I don't know if it's possible to share it with anybody.
I will be back soon!

OK Try going to this address [http://ubuntuone.com/5WxFmWVhGAlqxeRPsepPZl](http://ubuntuone.com/5WxFmWVhGAlqxeRPsepPZl)
Then download, double click to uncompress and copy the contents into /usr/share/icons
You may have to change the ownership, just select all (Ctrl+A) then right click and use the "permissions" Tab. Change it to your username
These icons were from my install of 11.10

---

### Post by grahammechanical on 2012-03-09
For those that do not know, the command **rm** = remove. It deletes but now you know that. Who of us has never learned something the painful way? If we haven't then we will one day.

I think the command you need is

> sudo nautilus

This will open the File Manager with administrator privileges. This will let you copy and paste into system folders. May be even drag and drop. BUT be careful. You will also be able to delete system files and folders as well.

Regards.

---

### Post by louisgonick on 2012-03-09
> **coldraven said:**
> I just compressed the contents of /usr/share/icons and am try to upload it to Ubuntu One.
I have never used it before so I don't know if it's possible to share it with anybody.
I will be back soon!

OK Try going to this address [http://ubuntuone.com/5WxFmWVhGAlqxeRPsepPZl](http://ubuntuone.com/5WxFmWVhGAlqxeRPsepPZl)
Then download, double click to uncompress and copy the contents into /usr/share/icons
You may have to change the ownership, just select all (Ctrl+A) then right click and use the "permissions" Tab. Change it to your username
These icons were from my install of 11.10

I am running Ubuntu from a live CD, already did a backup of all my files, but I cant copy the icons you sent me into usr/share/icons. I dont have the permission, there is a way to fix this, but trying to find a solution is what caused the problem in the first place. 

since I am running on a CD I cant install any software

---

### Post by louisgonick on 2012-03-09
I already checked and the icons are already where they are supposed to be and I still cant use ubuntu. I boot up and it freezes and there are almost no icons (not oven on the top bar).

I dualboot with windows on my laptop. 

Any tutorial on re-installing Ubuntu?

---

### Post by coldjeanz on 2012-03-10
just for reference if all you were trying to do was install a new icon set you really aren't supposed to add any to the root folders, you just make a folder named ".icons" in home folder and put the icon sets in there. then apply them with Gnome Tweak Tool.

---

### Post by Elfy on 2012-03-10
> **louisgonick said:**
> I already checked and the icons are already where they are supposed to be and I still cant use ubuntu. I boot up and it freezes and there are almost no icons (not oven on the top bar).

I dualboot with windows on my laptop. 

Any tutorial on re-installing Ubuntu?

_Once you have done all your backups._

Start the installer - once it reaches the partition part - choose something else.

You should see which partition are the linux ones - you can safely ignore the swap partition, that will just get recognised and used.

Select the other linux partition - edit - on the new screen choose / as the mountpoint. _Do not format._

This _should_ install and keep the /home safe. Use the same user name as you did previously

If you have more than one linux partition and are not at all sure which is which - don't carry on but give us the results of 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


[http://askubuntu.com/questions/247/whats-your-recommendation-on-drive-partitioning-schemes-for-a-desktop-and-home/3603#3603](http://askubuntu.com/questions/247/whats-your-recommendation-on-drive-partitioning-schemes-for-a-desktop-and-home/3603#3603)
[http://ubuntuforums.org/showthread.php?t=1558960](http://ubuntuforums.org/showthread.php?t=1558960)

---

### Post by louisgonick on 2012-03-10
> **forestpiskie said:**
> _Once you have done all your backups._

Start the installer - once it reaches the partition part - choose something else.

You should see which partition are the linux ones - you can safely ignore the swap partition, that will just get recognised and used.

Select the other linux partition - edit - on the new screen choose / as the mountpoint. _Do not format._

This _should_ install and keep the /home safe. Use the same user name as you did previously

If you have more than one linux partition and are not at all sure which is which - don't carry on but give us the results of 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


[http://askubuntu.com/questions/247/whats-your-recommendation-on-drive-partitioning-schemes-for-a-desktop-and-home/3603#3603](http://askubuntu.com/questions/247/whats-your-recommendation-on-drive-partitioning-schemes-for-a-desktop-and-home/3603#3603)
[http://ubuntuforums.org/showthread.php?t=1558960](http://ubuntuforums.org/showthread.php?t=1558960)

I tried boot up on a live CD, the first time I tried I was stuck on the initial black screen. I tried to reboot and now my computer won't even turn on..... 

update: problem solved, it boots up now

---

### Post by Gremlinzzz on 2012-03-10
> **louisgonick said:**
> I already checked and the icons are already where they are supposed to be and I still cant use ubuntu. I boot up and it freezes and there are almost no icons (not oven on the top bar).

I dualboot with windows on my laptop. 

Any tutorial on re-installing Ubuntu?

dual boot did you do side by side or wubi
which windows did you dual boot with

---

### Post by louisgonick on 2012-03-10
> **Gremlinzzz said:**
> dual boot did you do side by side or wubi
which windows did you dual boot with

I run vista, I already managed to make my laptop to turn on. I dualboot with GRUB. I am currently running  ubuntu from a live CD.

---

### Post by Gremlinzzz on 2012-03-10
Did you retrieve the docs you wanted/boot into vista
if so go to vistas disk management 
delete the Linux partitions
then reformat the partition NTFS
After this resize your drive to reclaim the space
Now we come to the tricky bit you will need to repair Vista bootloader or reinstall ubuntu.
Reboot your PC with the Vista DVD. When it gets to the Install now screen there is another option to repair your computer select that, go into command prompt and type in 
bootrec.exe /fixmbr

And thats it, remove the Vista DVD and reboot:popcorn:
 to reinstall ubuntu you can skip the tricky bit just put ubuntu cd in and reboot

---

### Post by Elfy on 2012-03-10
I thought OP wanted to reinstall after an error not remove it completely, not sure why they'd need to start fiddling with the existing partitions?

---

### Post by louisgonick on 2012-03-10
> **forestpiskie said:**
> I thought OP wanted to reinstall after an error not remove it completely, not sure why they'd need to start fiddling with the existing partitions?

Exactly, I don't even have a vista DVD laying around here. My laptop came with it installed.

---

### Post by Gremlinzzz on 2012-03-10
> **louisgonick said:**
> Exactly, I don't even have a vista DVD laying around here. My laptop came with it installed.

OK.wasn't sure what you had thought they gave everyone a Vista dvd.

---

### Post by Gremlinzzz on 2012-03-10
> **forestpiskie said:**
> I thought OP wanted to reinstall after an error not remove it completely, not sure why they'd need to start fiddling with the existing partitions?

That would be for a clean removal and/or a reinstall of Ubuntu:popcorn:

---

### Post by louisgonick on 2012-03-10
> **Gremlinzzz said:**
> That would be for a clean removal and/or a reinstall of Ubuntu:popcorn:

I have a question, will just following the steps the other person gave me will I be fine?

---

### Post by Gremlinzzz on 2012-03-10
> **louisgonick said:**
> I have a question, will just following the steps the other person gave me will I be fine?

forestpiskie is very qualified:popcorn:

---

### Post by louisgonick on 2012-03-10
> **forestpiskie said:**
> _Once you have done all your backups._

Start the installer - once it reaches the partition part - choose something else.

You should see which partition are the linux ones - you can safely ignore the swap partition, that will just get recognised and used.

Select the other linux partition - edit - on the new screen choose / as the mountpoint. _Do not format._

This _should_ install and keep the /home safe. Use the same user name as you did previously

If you have more than one linux partition and are not at all sure which is which - don't carry on but give us the results of 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


[http://askubuntu.com/questions/247/whats-your-recommendation-on-drive-partitioning-schemes-for-a-desktop-and-home/3603#3603](http://askubuntu.com/questions/247/whats-your-recommendation-on-drive-partitioning-schemes-for-a-desktop-and-home/3603#3603)
[http://ubuntuforums.org/showthread.php?t=1558960](http://ubuntuforums.org/showthread.php?t=1558960)

Once I choose something else and chose my old Linux partition, when I want to start installing it tells me "no root file system is defined. Please correct this from the partitioning menu" 
On device for boot loader installation I chose my whole hard drive, not a partition. The options available there are Vista and Ubuntu. Should I leave my whole drive selected it chose Ubuntu?

---

### Post by Elfy on 2012-03-10
> **Gremlinzzz said:**
> forestpiskie is very qualified:popcorn:

I hide my beans for a reason ... might be a mod - but there are many here that'll run rings around me :)

---

### Post by Elfy on 2012-03-10
> **louisgonick said:**
> Once I choose something else and chose my old Linux partition, when I want to start installing it tells me "no root file system is defined. Please correct this from the partitioning menu" 
On device for boot loader installation I chose my whole hard drive, not a partition. The options available there are Vista and Ubuntu. Should I leave my whole drive selected it chose Ubuntu?

You need to edit partition - then choose / as mountpoint.

_As long as you are sure it is the right partition._

If you have any doubts at all run 

```
sudo fdisk -l 
```

and post it here

---

### Post by louisgonick on 2012-03-10
> **forestpiskie said:**
> You need to edit partition - then choose / as mountpoint.

_As long as you are sure it is the right partition._

If you have any doubts at all run 

```
sudo fdisk -l 
```and post it here

Do I edit the partition and do the changes from the installer?

Here are the results of the commands:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x678b1560

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   387093871   193546904+   7  HPFS/NTFS/exFAT
/dev/sda2       465567744   488390655    11411456    7  HPFS/NTFS/exFAT
/dev/sda3       387094526   465567743    39236609    5  Extended
/dev/sda5       387094528   461514751    37210112   83  Linux
/dev/sda6       461516800   465567743     2025472   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Elfy on 2012-03-10
Select sda5 - edit partition - in the mountpoint box select /

Do _not_ format it - exit that window and you'll be back at the partiton list.

I assume you have your backups now - just in case. 

> Do I edit the partition and do the changes from the installer?Yes.

---

### Post by louisgonick on 2012-03-10
Just finished re installing Ubuntu, the screen resolution is something like 800x600 (horrible) icons are STILL blank, neither my touchpad or my mouse work, my wifi card is not recognized, I cant even access system settings. ](*,)

Right now I'm on windows because Ubuntu is STILL useless.

I appreciate any help and ideas.

---

### Post by louisgonick on 2012-03-10
> **forestpiskie said:**
> Select sda5 - edit partition - in the mountpoint box select /

Do _not_ format it - exit that window and you'll be back at the partiton list.

I assume you have your backups now - just in case. 

Yes.

I just found this site with instructions on how to re install..
apparently what would help will be a clean re install.

Will post updates

---

### Post by louisgonick on 2012-03-10
SUCCESS! :D

I had to do a clean install of Ubuntu. I had to start from zero. Luckily I did a backup. 

Thanks to everyone!

---

