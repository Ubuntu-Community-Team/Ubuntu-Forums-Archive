---
title: "Installation advice"
date: 2006-02-28
forum: General Help
---

### Post by cabber on 2006-02-28
First post and appreciate the assistance.

I'm building a new system and want the ability to use Ubuntu and Windows XP.  That said, I have three HDs (250G, 36G, 250G).  What is the best way to set this up?  I would prefer to have Ubuntu and Windows on seperate drives.  And use the third drive for back up.  Which OS should I install first and do I need the Grub to boot into each?  Should I install Ubuntu with a FAT32 partition?  Since it would be on its own drive does it matter if Windows is in NTFS on one drive and Ubuntu is FAT32?  So many questions.  Thanks.

---

### Post by cabber on 2006-02-28
Related to the above:

On a side note, I would like to share the information from a back up drive (3rd drive) to both Windows and Ubuntu.  Please advise.  Thank you.

---

### Post by Sutekh on 2006-02-28
[QUOTE=cabber]First post and appreciate the assistance.

I'm building a new system and want the ability to use Ubuntu and Windows XP.  That said, I have three HDs (250G, 36G, 250G).  What is the best way to set this up?  I would prefer to have Ubuntu and Windows on seperate drives.[/QUOTE]This should simplify things for you.  [QUOTE=cabber]And use the third drive for back up.[/QUOTE] Which one is that going to be?  The 36GB?[QUOTE=cabber]Which OS should I install first and do I need the Grub to boot into each?[/QUOTE]Install Windows first, then Ubuntu, with two drives it doesn't really make much of a difference though.  You will need the GRUB or a similar boot manager to be able to boot into either OS.  If you install Ubuntu second, the GRUB can detect all your installed OS and setup things nicely for you.[QUOTE=cabber]Should I install Ubuntu with a FAT32 partition?[/QUOTE]You should install Ubuntu on a native Linux filesystem, like **ext3**.  You can create an extra partition that is formatted FAT32, to which both Windows and Ubuntu can access.  [QUOTE=cabber]Since it would be on its own drive does it matter if Windows is in NTFS on one drive and Ubuntu is FAT32?  So many questions.  Thanks.[/QUOTE]
It's a lot easier (IMO) when Windows and Ubuntu are on separate drives.  So just go for it.  

Here's some nice graphical install guides to give you an idea of the installation process.

These two are good for when you want to fit Ubuntu and Windows on the *same* drive

[http://users.bigpond.net.au/hermanzone/p2.htm]("http://users.bigpond.net.au/hermanzone/p2.htm") Ubuntu + FAT Installation

[http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm") - Ubuntu + NTFS Installation

This one is good for a simple install (the one I would recommend for your situation)
[http://mrbass.org/linux/ubuntu/install/]("http://mrbass.org/linux/ubuntu/install/")

---

### Post by Sutekh on 2006-02-28
[QUOTE=cabber]Related to the above:

On a side note, I would like to share the information from a back up drive (3rd drive) to both Windows and Ubuntu.  Please advise.  Thank you.[/QUOTE]
In this case, you will need to format that drive FAT32, to be able to share it between Windows and Ubuntu

---

### Post by cabber on 2006-02-28
[QUOTE=Sutekh]This should simplify things for you.   Which one is that going to be?  The 36GB?Install Windows first, then Ubuntu, with two drives it doesn't really make much of a difference though.  You will need the GRUB or a similar boot manager to be able to boot into either OS.  If you install Ubuntu second, the GRUB can detect all your installed OS and setup things nicely for you.You should install Ubuntu on a native Linux filesystem, like **ext3**.  You can create an extra partition that is formatted FAT32, to which both Windows and Ubuntu can access.  
It's a lot easier (IMO) when Windows and Ubuntu are on separate drives.  So just go for it.  

Here's some nice graphical install guides to give you an idea of the installation process.

These two are good for when you want to fit Ubuntu and Windows on the *same* drive

[http://users.bigpond.net.au/hermanzone/p2.htm]("http://users.bigpond.net.au/hermanzone/p2.htm") Ubuntu + FAT Installation

[http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm") - Ubuntu + NTFS Installation

This one is good for a simple install (the one I would recommend for your situation)
[http://mrbass.org/linux/ubuntu/install/]("http://mrbass.org/linux/ubuntu/install/")[/QUOTE]

First off, thank you for your assistance.

I am a bit ignornant coming from the Windows camp on partitioning.  What is ext3? And how do I create a partition in the way?  Do I need a partitioning software?  Also, once WIndows is installed, and I start installing Ubuntu on the second drive, should I let the installer do the partitioning?  Thanks again.

---

### Post by cabber on 2006-02-28
By the way, these drives are all connected to internal SATA connections.  Does that pose issues?

---

### Post by cabber on 2006-02-28
[QUOTE=Sutekh]In this case, you will need to format that drive FAT32, to be able to share it between Windows and Ubuntu[/QUOTE]

I'll be installing Windows on a 250G SATA Drive first (NTFS).  I'll put Ubuntu on the 37G SATA drive second.  Do I partition that drive with the Ubuntu installation program?  If so, should I make it FAT32 or NTFS?  I'll use the third drive for Backup and sharing for both OS's.  Again, should I partition that drive in Windows or Ubuntu?

When I installed Ubuntu  just to test, it seemed like it had a few different options to partition/format drives.

---

### Post by Bachstelze on 2006-02-28
As it was said before, The drive you install Ununtu on should be neither NTFS nor FAT32, it **must** be ext3, which is the native linux filesystem.

So you just install Windows on your first drive and then format the third one as FAT32 from Windows (right click > Format in My Computer) and do nothing to the second, you will partition it during the Ubuntu installation.

---

### Post by cabber on 2006-02-28
[QUOTE=HymnToLife]As it was said before, The drive you install Ununtu on should be neither NTFS nor FAT32, it **must** be ext3, which is the native linux filesystem.

So you just install Windows on your first drive and then format the third one as FAT32 from Windows (right click > Format in My Computer) and do nothing to the second, you will partition it during the Ubuntu installation.[/QUOTE]


I'm installing Ubuntu right now.  Its at the partitioning area of the loading process.

Which selection do I make?
Erase entire disk:
or
Erase entire disk and use LVM

Thanks

---

### Post by Bachstelze on 2006-02-28
I would recomment maual partitioning. Create 3 partitions :

one for the root filesystem (/) of about 10 GB
a swap partition of 1,5 GB
all the rest as a /home partition

If you want step-by-step instructions, just ask :)

---

### Post by cabber on 2006-02-28
[QUOTE=cabber]I'm installing Ubuntu right now.  Its at the partitioning area of the loading process.

Which selection do I make?
Erase entire disk:
or
Erase entire disk and use LVM

Thanks[/QUOTE]
  I figured it out.  Went with choice one.  Thanks.

---

### Post by cabber on 2006-02-28
[QUOTE=HymnToLife]I would recomment maual partitioning. Create 3 partitions :

one for the root filesystem (/) of about 10 GB
a swap partition of 1,5 GB
all the rest as a /home partition

If you want step-by-step instructions, just ask :)[/QUOTE]


Thanks for jumping in.  You guys are awesome.  To your suggestion:  WHy would you do this and please provide a step by step process.  Thanks.

As of now, I just erase the entire disk and created no additional partitions, but I can always reinstall

---

### Post by cabber on 2006-02-28
While you are in the educating mind frame.  i had problems with an initial trial install: (graphical load) with the xserver.  I have a Radeon X1800XT vid card which I would assume is the culprit.  I ended up manual switching to the VESA driver and had it working.  Resolution was not proper, but it worked.  I read an entire guide to installing Radeon drivers, but couldn't understand a few of the steps.  Most important was wher to enter the settings.  Do you just open a terminal window and start typing from the instructions?

---

### Post by Bachstelze on 2006-02-28
Basically the onlydifferent thing is the /home partition. It's better to have it on a different partition because it's where all your documents and settings will be stored. So if you format your / Partition to reinstall Ubuntu (or another Linux system), all of it will still be here.

So, go to the manual partitioning, you will have a screen like [this ](http://www.pcentraide.com/tutoriel/dual-boot/dual-boot-linux-windows-5.jpg) (sorry, this one is french). So you move your cursor onto the "Free space" line, press enter, enter the size (10 GB), define it as a primary partition at the beginning of the disk, you have nothing to change in the last screen so hit "Done". Then you create your swap partition the same way (1,5 GB - logical - beginning), in the last screen, hit "Use as" > swap area then Done. Finally create your thid partition, logical. On the last screen,the /home mount point should be selected by default. In the end you should have something like [that](http://www.pcentraide.com/tutoriel/dual-boot/dual-boot-linux-windows-6.jpg) (except for the NTFS partition), if so you can Finish and write changes to disk :)


For you ATI drivers thing, can you post a link to the tutorial ?

---

### Post by Sutekh on 2006-02-28
[QUOTE=cabber]Thanks for jumping in.  You guys are awesome.  To your suggestion:  WHy would you do this and please provide a step by step process.  Thanks.

As of now, I just erase the entire disk and created no additional partitions, but I can always reinstall[/QUOTE]
If you have a whole hard disc for Ubuntu (which you did) and you are very new to Linux (which you are), option one - **Erase entire disk** was the right choice for now.

Later you can try the other way HymnToLife suggested if you want a more personalised install, [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm") will show you how to manually partition (steps 14 onwards give the general idea, looks at the pics).  Basically it works in steps, and please note this is the general way to do it and I'm only going off those pictures in the guide and my memory...


 - Choose to **Manually Edit** the partition table

 - To create the root filesystem (check this link for an explanation on the filesystem structure [Ubuntu Forums - That crazy directory tree!]("http://www.ubuntuforums.org/showthread.php?t=126107"))

[LIST]
[*]Choose some **Free Space** and **Create a new partition**
[*]In the partition settings, in **Use as** choose **ext3**
[*]In **Mount point** choose **/** - This is the root filesystem
[*]In **Size** choose whatever you think appropriate (10GB is fine)
[*]Choose **Done setting up the partition**)
[/LIST]

 - To create some swap space

[LIST]
[*]Choose some **Free Space** and **Create a new partition**
[*]In the partition settings, in **Use as** choose **swap**
[*]In **Mount point** choose **/swap** (I think does this automatically)
[*]In **Size** choose whatever you think appropriate (1.5 - 2 times your RAM should be okay)
[*]Choose **Done setting up the partition**)
[/LIST]

 - To create a /home partition

[LIST]
[*]Choose some **Free Space** and **Create a new partition**
[*]In the partition settings, in **Use as** choose **ext3**
[*]In **Mount point** choose **/home**
[*]In **Size** it should choose whatever is left over.
[*]Choose **Done setting up the partition**)
[/LIST]

---

### Post by Sutekh on 2006-02-28
[QUOTE=HymnToLife]So, go to the manual partitioning, you will have a screen like [this ](http://www.pcentraide.com/tutoriel/dual-boot/dual-boot-linux-windows-5.jpg) (sorry, this one is french). So you move your cursor onto the "Free space" line, press enter, enter the size (10 GB), define it as a primary partition at the beginning of the disk, you have nothing to change in the last screen so hit "Done". Then you create your swap partition the same way (1,5 GB - logical - beginning), in the last screen, hit "Use as" > swap area then Done. Finally create your thid partition, logical. On the last screen,the /home mount point should be selected by default. [/QUOTE]
Actually I think HymnToLife is right, it will choose the mount points by default (starting with / then /home) so you won't need to select it yourself

---

### Post by cabber on 2006-02-28
[QUOTE=HymnToLife]Basically the onlydifferent thing is the /home partition. It's better to have it on a different partition because it's where all your documents and settings will be stored. So if you format your / Partition to reinstall Ubuntu (or another Linux system), all of it will still be here.

So, go to the manual partitioning, you will have a screen like [this ](http://www.pcentraide.com/tutoriel/dual-boot/dual-boot-linux-windows-5.jpg) (sorry, this one is french). So you move your cursor onto the "Free space" line, press enter, enter the size (10 GB), define it as a primary partition at the beginning of the disk, you have nothing to change in the last screen so hit "Done". Then you create your swap partition the same way (1,5 GB - logical - beginning), in the last screen, hit "Use as" > swap area then Done. Finally create your thid partition, logical. On the last screen,the /home mount point should be selected by default. In the end you should have something like [that](http://www.pcentraide.com/tutoriel/dual-boot/dual-boot-linux-windows-6.jpg) (except for the NTFS partition), if so you can Finish and write changes to disk :)


For you ATI drivers thing, can you post a link to the tutorial ?[/QUOTE]


So right now after the Ubuntu install process I have:

**XIO:  Fatal IO Error 104 (connection reset by peer) on Xserver ":0.0" after 0 request (o known processed) with o events remaining.**

I had this before a was able to type in some xserver setting to manually change the video settings to **VESA** and was able to boot into the OS.  The resolution was wrong though.

Here are the links I have been reading.
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by Bachstelze on 2006-02-28
Yes, all of the commands are to be run in a terminal window.

---

### Post by cabber on 2006-02-28
[QUOTE=HymnToLife]Yes, all of the commands are to be run in a terminal window.[/QUOTE]


So I ran this command:

[B]sudo dpkg-reconfigure xserver-xorg

set driver to 'vesa', and when setting resolution, give yourself 1024 x 768[/B]

and I'm able to boot into the OS.  Now I'm sure the fun starts:confused:

---

