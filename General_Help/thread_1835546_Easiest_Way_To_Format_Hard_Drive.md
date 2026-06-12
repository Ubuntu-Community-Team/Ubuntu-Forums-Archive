---
title: "Easiest Way To Format Hard Drive?"
date: 2011-08-29
forum: General Help
---

### Post by johnsmoke on 2011-08-29
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Ok, so I installed Ubuntu last night, prior to the install I had problems with booting up Vista etc... I couldn't boot it. What I should have done was wipe out my hard drive/format it and do a fresh clean install of Ubuntu. So, my question is, at this point, what is the quickest/easiest way for me to format my hard drive so that I can do a fresh new install of Ubuntu? [/SIZE][/FONT]
[/SIZE][/FONT]

---

### Post by seawolf167 on 2011-08-29
Pop in your Ubuntu disk, boot off it, then when you are at the partitioning step, select to manually partition, then delete the current partition table and re-create as you want (i.e. root partition, /home partition, swap partition, etc.)

---

### Post by spiky001 on 2011-08-29
Hi you can use Gparted which is on the Ubuntu cd you can boot the live cd and format and partition the drive to how you want it, Although when you install You will be formatting the drive at the same time

---

### Post by johnsmoke on 2011-08-29
You know I think I just found an answer to my own question! It looks like I can create an ISO image disc of DBAN, then boot from the DBAN cd... wipe everything, then do my fresh, clean install of Ubuntu! Sorry for the post when I was able to locate the information.

---

### Post by seawolf167 on 2011-08-29
Thats too many steps! Any linux live cd shouldn't have a problem formatting and partitioning hard drives for you (including the Ubuntu install cd). You can just have the installer take care of it as I mention above.

---

### Post by johnsmoke on 2011-08-29
> **seawolf167 said:**
> Thats too many steps! Any linux live cd shouldn't have a problem formatting and partitioning hard drives for you (including the Ubuntu install cd). You can just have the installer take care of it as I mention above.
 
 
I see what you mean. I believe I did try to use Gparted last night to do that and it said something like "no devices detected" when I tried to run it. Not sure why it wasn't detecting my hard drive. Then I just installed Ubuntu and selected the option to install Ubuntu without keeping Windows. However, I am still getting some boot issues from when I had Windows installed. So I'd like to just completely wipe out/format the hard drive and do a clean/fresh install of Ubuntu. I will follow your instructions, boot from the Ubuntu live CD and give it a shot.

---

### Post by johnsmoke on 2011-08-29
> **seawolf167 said:**
> Thats too many steps! Any linux live cd shouldn't have a problem formatting and partitioning hard drives for you (including the Ubuntu install cd). You can just have the installer take care of it as I mention above.
 
OH, hold on! Sorry, I just re-read your post and I see that you are saying to do actually do it all from the installation? So just plug in the Ubuntu Live CD, and select Install (I won't have a problem doing this even though Ubuntu is already installed?), then there should be an option somewhere within the installation process to manually partition?

---

### Post by seawolf167 on 2011-08-29
Don't use the installer suggested sizes - in my experience it create wayyy to large a swap partition. When you get to manually defining the partition table, something like this should be fine

mount point : format type : size
/ : ext4 : 10 GB
swap : swap : 2 GB
/home : ext4 : remainder

---

### Post by seawolf167 on 2011-08-29
> **johnsmoke said:**
> then there should be an option somewhere within the installation process to manually partition?

Yes - it should be near the start of the install. Instead of selecting to "wipe and use the entire drive" or "install side-by-side", select to manually partition the drive then follow my previous post for partition mount points, types and sizes.

---

### Post by johnsmoke on 2011-08-29
> **seawolf167 said:**
> Don't use the installer suggested sizes - in my experience it create wayyy to large a swap partition. When you get to manually defining the partition table, something like this should be fine
 
mount point : format type : size
/ : ext4 : 10 GB
swap : swap : 2 GB
/home : ext4 : remainder
 
 
Ok, I will do it how you said. Certainly seems like the easiest way, and I thank you for that. Also, I'm new at partitioning drives etc... Why split it into 3 partitions? Why not just have the on Home partition, the full hard drive? Also what does swap stand for with the 2 gigs allocated to it? And what is the first one with the /:ext4? Sorry for all the questions, I've just never formatted  hard drive and I want to make sure I do it all properly tonight.

---

### Post by seawolf167 on 2011-08-29
mount point : format type : size
/ : ext4 : 10 GB          <----- this is the / (root) partition
swap : swap : 2 GB          <----- this is the swap partition
/home : ext4 : remainder          <----- this is the /home partition

The colons ":" are just used to separate entries, ext4 & swap are partition formats.

I suggest that you have separate /home and / (root) partitions so in the future if you want to reinstall (or something screws up your root partition), you *only* have to install the / (root) partition, all your personal configurations/settings/files/folders/music/pictures/etc. are safe and won't be touched (since they are contained in your /home partition)

---

### Post by Topsiho on 2011-08-29
Hello johnsmoke,

The answers you got are perfect, I agree with them.

You asked why three partitions and what they are used for.

1. / is the root partition. It is intended for all system files. When you reinstall this is the partition that holds the new system.

2. /home is for the personal files and settings. It is a subdirectory of / but having it in a partition of it's own, you can leave it as it is (only set its mountpoint to /home again) when doing a reinstall. In that way your precious personal files and settings will be preserved. ALLWAYS DO A BACKUP though of the files you don't want to loose.

3. The swap partition should be 2 times your RAM (working memory of the computer). To this swap contents of your RAM will be temporary moved when the memory is necessary for something else.

Also:

Nice to know that there are primary partitions, an extended partition, and logical partitions.

A disk can hold only 4 primary partitions, one of them may be an extended partition, and an extended partition can hold any (practical) number of logical partitions.

So to be prepared for the future, one could install / in a primary partition, and /home and swap in logical partitions (Ubuntu creates an extended partition automatically when you create the first logical partition).

So, now you can go agead. Have fun :)

Topsiho

---

### Post by johnsmoke on 2011-08-29
Thanks for the great advice guys! Now tonight will be much easier to do a fresh install of the great Unbutu!

---

### Post by seawolf167 on 2011-08-29
And once you get everything all up and running to your satisfaction, make a image of your drive using [Clonezilla ]("http://www.clonezilla.org")and store it on an external hard drive. Then if something breaks beyond repair you can just re-image your computer back to the state it was in when you made it (you don't even have to worry about boot records if you image the entire drive :) )

---

### Post by johnsmoke on 2011-08-29
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Thanks for the awesome advice Seawolf and everyone else. Just to clarify so I know what I'm doing tonight. I'm going to select to manually partition or "custom" or whatever it says in the installation process. Then at that point, I'll just select to delete each and every item that comes up in there as I want to start fresh, correct? At this point, I'm guessing there will be some sort of option I can click that says "create partition" or something. As far as creating the partitions, I believe they need to be entered in megabytes, correct? So 8 GB = 8,000 megabytes and so on... Will I need to manually name these with a forward slash / followed by home, swap, root etc..? Or will there be like a drop-down menu to select these? As far as format type, I see that the root is ext4, swap is swap, and home is ext 4... what exactly is ext 4? Shouldn't it be NTFS? These are the last questions I had about this, I just want to be sure I know what I'm doing while installing tonight. 
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by seawolf167 on 2011-08-29
> **johnsmoke said:**
> [FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]I'm going to select to manually partition or "custom" or whatever it says in the installation process.[/SIZE][/FONT][/SIZE][/FONT]

Yup, instead of selecting to install side-by-side or overwrite and use the entire disk, you can select to manually partition the disk. It might say "advanced" but it is pretty easy. After you do it once you'll wonder why you ever though it was complicated before.

> **johnsmoke said:**
> [FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]I'll just select to delete each and every item that comes up in there as I want to start fresh, correct? [/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

You should just be able to select "Create new partition table" instead of deleting each entry, but the only difference is speed (so 10 seconds versus 2 seconds? lol)

[/SIZE][/FONT][/SIZE][/FONT]> **johnsmoke said:**
> [FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]At this point, I'm guessing there will be some sort of option I can click that says "create partition" or something.[/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

Yes, its pretty self explanatory

[/SIZE][/FONT][/SIZE][/FONT]> **johnsmoke said:**
> [FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]As far as creating the partitions, I believe they need to be entered in megabytes, correct? So 8 GB = 8,000 megabytes and so on... [/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

Yup, so 100,000 = 100GB (it'll show numbers with a little graphical preview

[/SIZE][/FONT][/SIZE][/FONT]> **johnsmoke said:**
> [FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Will I need to manually name these with a forward slash / followed by home, swap, root etc..? Or will there be like a drop-down menu to select these? [/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

There is a drop down as for where you want it mounted, but you can also enter the partitions manually:

These are the mount points (*exactly *as listed on each line below)

/
/home
swap

[/SIZE][/FONT][/SIZE][/FONT]> **johnsmoke said:**
> [FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]As far as format type, I see that the root is ext4, swap is swap, and home is ext 4... what exactly is ext 4?[/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

ext4 is the current incarnation of the linux filesystem. It is the 4th version of the journaling extended filesystem for linux

[/SIZE][/FONT][/SIZE][/FONT]> **johnsmoke said:**
> [FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Shouldn't it be NTFS?[/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

NTFS is Windows' version of a hard drive format type. NTFS is ***BAD*** for a linux system as it cannot handle permissions (among various other things).[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by johnsmoke on 2011-08-29
Thanks man! You were absolutely right, it was a LOT easier than I thought it would be. SUPER simple. Thanks so much for all the advice. Ubuntu is great, I'm happy to ditch Vista! Thanks again! 



> **seawolf167 said:**
> Yup, instead of selecting to install side-by-side or overwrite and use the entire disk, you can select to manually partition the disk. It might say "advanced" but it is pretty easy. After you do it once you'll wonder why you ever though it was complicated before.

[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

You should just be able to select "Create new partition table" instead of deleting each entry, but the only difference is speed (so 10 seconds versus 2 seconds? lol)

[/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

Yes, its pretty self explanatory

[/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

Yup, so 100,000 = 100GB (it'll show numbers with a little graphical preview

[/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

There is a drop down as for where you want it mounted, but you can also enter the partitions manually:

These are the mount points (*exactly *as listed on each line below)

/
/home
swap

[/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

ext4 is the current incarnation of the linux filesystem. It is the 4th version of the journaling extended filesystem for linux

[/SIZE][/FONT][/SIZE][/FONT][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]

NTFS is Windows' version of a hard drive format type. NTFS is ***BAD*** for a linux system as it cannot handle permissions (among various other things).[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by seawolf167 on 2011-08-29
No problem! Please mark the thread as solved under thread tools now :)

Make sure to come back and post a new thread if you have any other questions that arise - most of the things you'll run into have simple solutions (like dvd playing - it doesn't work out of the box, but the solution is [very simple]("https://help.ubuntu.com/community/RestrictedFormats"), just install the restricted extras and run a script).

---

