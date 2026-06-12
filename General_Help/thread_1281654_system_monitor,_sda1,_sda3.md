---
title: "system monitor, sda1, sda3"
date: 2009-10-03
forum: General Help
---

### Post by macabrem on 2009-10-03
See the attached screenshot...

My computer came with Ubuntu preinstalled, so this may seem like a dumb question, but can somebody explain this screenshot and what the difference between the sda1 and sda3 folders are?  

Are these partitions?  Am I able to store files on both partitions?  How do I access the sda1 partition?  If I'm not supposed to add files to sda1, why does it have that much free space I can't use?

---

### Post by Roasted on 2009-10-03
/ is root, where the operating system is installed among other more crucial files. 

/home is your home directory, where all of your stuff resides.

The reason this is a smart idea to split them is if you need to reinstall Ubuntu for any reason, just pop the LiveCD in and do a manual editing of the partitions. From there you can check format for root and uncheck format for home. That means you can reinstall Ubuntu without losing your personal documents. You just have to make sure you specify format or do not format for the particular partitions at hand.

This is the exact way I have my system set up. I love it. Now when Ubuntu Karmic 9.10 comes out I can install it without anything happening to my home directory. But - as I said, just gotta make sure you do a manual install and check the format boxes accordingly so you don't have a big problem on your hands. ;)

---

### Post by ibuclaw on 2009-10-03
In a nutshell, to explain how partitions work.

There are two types of Hard Drives, **IDE** and **SCSI**. Almost all desktop hard drives are SCSI.
The way that Linux represents IDE drives on the system is the alias **hd**.
The way that Linux represents SCSI drives on the system is the alias **sd**.

Systems can support multiple hard drives to connect to the computer.
Last time I looked, Linux names them from **a** to **az**.

The first SCSI hard drive being: **sda**
The second SCSI hard drive being: **sdb**

A Hard Drive can have up to** 4 Primary Partitions**.
Linux represents these partition numbers as **1-4**.

The first primary partition on the first hard drive being: **sda1**
The third primary partition on the second hard drive being: **sdb3**

To work around the limit on partitions, there is such a thing as an **Extended Partition**, which can house up to **15 Logical Partitions** (last time I checked, may be more/unlimited).
Linux represents these partition numbers as **5-16**

The first logical partition on the first hard drive being: **sda5**
The third logical partition on the second hard drive being: **sdb7**


From what is being displayed on your screenshot:
[LIST=1]
[*]sda1 is the first primary partition on the first hard drive, and it is mounted on root ( / ).
Stored on here will be every application/boot/configuration file on your system.
[*]sda3 is the third primary partition on the first hard drive, and it is mounted on home ( /home ).
Stored on here will be all your personal files in your Home directory.
[/LIST]

This is alot to take in, but it is a very logical naming convention.

If you have any questions, just ask!

Regards
Iain

---

### Post by macabrem on 2009-10-03
Thanks for the help.  So, I should probably avoid trying to ever place files in the sda1 area even though there is free space, since that is where crucial stuff is at?

Why is it set up to have that much free space?

---

### Post by oldfred on 2009-10-03
Your root is only 13.8GB and most seem to recommend 10GB for a normal install as a minimum with maybe 4GB or so used. All the programs/applications you install will be in root, so if you decide to install a lot of stuff it can take up some space. Also log files and other system stuff will grow over time so you have room to let it grow for quite a while before you have to worry about housecleaning old stuff.

Your /home is 131.1GB so it has lots of room for your data. But music, movies, photos, data all can consume that fairly quickly.

---

### Post by bunorama on 2009-10-03
You can install linux with /home under / so there is no separate partition.
They separate it for a couple reasons.
1. So your root partition doesn't get filled up by personal data.
2. When reinstalling, you can reformat the / without losing your /home

If you were running a 1000 user organization, it would be very good to have them on separate partitions, more likely separate drives.  For home use, the advantage is not so much.

The minimal install for linux is 2 partitions, / and SWAP.

---

### Post by sopadeajo on 2009-10-03
[IMG]http://i38.tinypic.com/2h7dgth.jpg[/IMG]

Here is an example (in the snap) of my dual system Vista/Jaunty.
How to use in the simpler manner GParted to separate Home folder so that when upgrading to Karmic, personal configurations do not get lost ?


[IMG]http://es.tinypic.com/r/fn8ig8/4[/IMG]

[IMG]http://es.tinypic.com/r/fn8ig8/4[/IMG]

[IMG]http://img401.imageshack.us/img401/2312/screenshotdevsdag[/IMG]

[IMG]http://img121.imageshack.us/img121/2312/screenshotdevsdag[/IMG]

---

### Post by Roasted on 2009-10-03
I wouldn't worry about application size, for the record. I have a 20gb root directory with every application installed I would ever hope and dream of using and I'm only using 5.6gb in my root directory. 

And it's not that you should AVOID anything in the root directory, it's just your home directory is where you normally store your personal stuff. Music, videos, pictures, documents, etc.

Your home directory in Linux is EXACTLY like your My Documents folder in Windows. You store all of YOUR stuff here, whereas programs and whatnot get stored elsewhere.

It's just a nice feature to have due to the high frequency of rollouts Ubuntu does, with a new version coming out every 6 months. Sure, you can upgrade, but the vast majority of users out there prefer a clean, fresh install. Having your home directory on a separate partition makes upgrading with a fresh install to the new version of Ubuntu much easier since you can do so without nuking all of your personal files too.

---

### Post by bunorama on 2009-10-03
sopadeajo, you'll need to copy what you want from /home to a drive or partition that wont be formatted for the new install.  After copy, verify all the data is there, because if you don't have permission to access something, it won't copy.   And when you install, it will show what it is going to do, make sure it doesnt want to destroy your copy.

For the linux install size, I started with 20g, but mostly linux uses less then 10g for what I do.  But then I installed vmware server and it was saving some things on my linux drive (tho my vm storage was elsewhere) so I went to a 60g for VM (temp files I guess).   And when I resized the 10g -> 60g with gparted, it messed up grub or mbr or something, which cost me another evening researching linux nonsense.  

Point is, be careful.  Linux is frail and cobbled together, it is meant for engineers, not the casual home user.

---

