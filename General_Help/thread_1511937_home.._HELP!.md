---
title: "/home.. HELP!"
date: 2010-06-17
forum: General Help
---

### Post by Sharang.d on 2010-06-17
It's my umnn maybe 10th day into Ubuntu and I've been reading the forums and doing stuff on my pc for like 8 hours daily :S [My point being that I'm in love with it :P] 
So anyway, I came across many people saying "blah blah....my /home is in another seperate partition.....blah bah" and i tried searching the various guides (posted in members' signatures), forums too with keywords like "/home directory" , "/home location" , "changing /home" , etc but failed to stumble upon any interesting information regarding /home!

So i would like to ask my questions here itself :
1. How do you change it?
2. WHY!?!?
3. Do you really store data in it?
4. WHY!?!? Why not on any normal mounted volume?

Thank you :)

---

### Post by tendonstrength on 2010-06-17
Check this out: 

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

It will give you the rationale behind different partitioning schemes including info on the /home directory.

---

### Post by philinux on 2010-06-17
> **Sharang.d said:**
> It's my umnn maybe 10th day into Ubuntu and I've been reading the forums and doing stuff on my pc for like 8 hours daily :S [My point being that I'm in love with it :P] 
So anyway, I came across many people saying "blah blah....my /home is in another seperate partition.....blah bah" and i tried searching the various guides (posted in members' signatures), forums too with keywords like "/home directory" , "/home location" , "changing /home" , etc but failed to stumble upon any interesting information regarding /home!

So i would like to ask my questions here itself :
1. How do you change it?
2. WHY!?!?
3. Do you really store data in it?
4. WHY!?!? Why not on any normal mounted volume?

Thank you :)

Easiest to do it from a clean install. However it can be done retrospectively. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Why. It makes reinstalling a doddle. You choose manual install and don't mark /home to be formatted. 

You could just have a data partition and leave home just for config files. You would have to back these up to restore them after a reinstall.

I do store data in mine. I've reinstalled maybe 6 times and my customisations and app settings remain.

I have this setup.

/ 12 gig
/swap 2 gig, as I have 2 gig of ram
/home the rest of the drive.

---

### Post by Sharang.d on 2010-06-17
> **tendonstrength said:**
> Check this out: 

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

It will give you the rationale behind different partitioning schemes including info on the /home directory.

Ok. Hold on. Reading :)

---

### Post by doas777 on 2010-06-17
I'd go with Phil's advice. the psychocats tutorials are usually very good, and i've used that one before.

my personal advice, is that installing ubuntu a few times is good for you, so if you are just getting started, you'll probably rebuild a few times before you have your process down.

---

### Post by Sharang.d on 2010-06-17
> **philinux said:**
> Easiest to do it from a clean install. However it can be done retrospectively. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Why. It makes reinstalling a doddle. You choose manual install and don't mark /home to be formatted. 

You could just have a data partition and leave home just for config files. You would have to back these up to restore them after a reinstall.

I do store data in mine. I've reinstalled maybe 6 times and my customisations and app settings remain.

I have this setup.

/ 12 gig
/swap 2 gig, as I have 2 gig of ram
/home the rest of the drive.

What exactly does /home contain? Cuz mine is just 64kb  :confused:
How do i see the size of my swap? [Also, how do i set it as per my preference?]

EDIT:
umnn and also how do i set the location of /home during install? Don't think i ever got that option while installing..

---

### Post by dabl on 2010-06-17
> **Sharang.d said:**
> What exactly does /home contain?



Whatever you choose to save in it, plus the settings for all your GUI packages.  The settings are in "hidden" files and folders -- you can see them if you set the "View" to "Show hidden files" on your file manager, or use ```
ls -la
``` in the console.

> 
How do i see the size of my swap? [Also, how do i set it as per my preference?]


In the console, ```
sudo fdisk -lu
``` will show you the size of your swap partition in blocks, and ```
du -h
``` will show it in KBytes.

Unless you have reason to suspect there's a problem, I wouldn't advise fiddling with the size of it.  GParted is the tool to use if an adjustment is needed.

---

### Post by philinux on 2010-06-17
> **Sharang.d said:**
> What exactly does /home contain? Cuz mine is just 64kb  :confused:
How do i see the size of my swap? [Also, how do i set it as per my preference?]

EDIT:
umnn and also how do i set the location of /home during install? Don't think i ever got that option while installing..

On a clean install I wouldn't expect home to contain much at all. Never checked with properties.

One way to see the size of swap is to use sys>admin>system monitor. Resources tab.

A default install will not ask about home. You have to use Specify Partitions manually.

---

### Post by beckols on 2010-06-17
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

^a little extra info on swap

/home contains all of the users' personal directories (Desktop, Documents, Pictures, etc.) and configuration files that are specific to a user (firefox profile, login options/aliases, et al).  Your home directory would be /home/sharang (or whatever your username is).

---

### Post by philinux on 2010-06-17
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Scroll down to see the manual partitioning example.

---

### Post by SoFl W on 2010-06-17
Try this thread:
[http://ubuntuforums.org/showthread.php?t=1411215](http://ubuntuforums.org/showthread.php?t=1411215)

---

### Post by Sharang.d on 2010-06-17
@
dabl
philinux
beckols
SoFl W

The links helped, thanks!
I'm not making this thread as "Solved" as of now. Will be installing the x64 version of 10.04 Ubuntu tomorrow which is when i'll make seperate partions for /home and /swap and I'm kinda convinced I'm gonna need more help about this soon :(

---

### Post by philinux on 2010-06-17
> **Sharang.d said:**
>  Will be installing the x64 version of 10.04 Ubuntu tomorrow which is when i'll make seperate partions for /home and /swap and I'm kinda convinced I'm gonna need more help about this soon :(

Sounds like FUN! :mrgreen:

---

### Post by Sharang.d on 2010-06-17
> **philinux said:**
> Sounds like FUN! :mrgreen:
Heh..
Anyway, temme what you think about this setup :
I have pre-installed XP and 4 partitions are currently made which cannot be changed and/or used (I need to keep XP for my family members to check mail, etc.). So i have one partition of 343GB and the current 20gb volume in which I've installed the current Linux for doing the following: 
Now can i do this..
/swap=2gb
/        =20gb
/home=[Suggest please. Ps: I'm not gonna store any data in it.. just the settings that are stored by default]
/New_Drive=Rest of the space but in NTFS Format

{My total HDD Size = 500 Gbs}

Which file system should /swap, /home, / have?
Also, Should I be able to access the aforementioned 4 partitions + the New_drive in XP?
I really wouldn't mind if any of the Linux partitions cannot be accessed in XP.
Looking forward to your reply. :)

---

### Post by doas777 on 2010-06-17
well, I would recomend that your swap be at least the size of your physical ram; otherwise you can;t hibernate.

Swap is it's own File System type so just pull down the list and select SWAP. you don;t need to provide a mountpoint or format swap.

your home is where most of your files will go by default but if you want to minimize it, 5GB would probably be sufficient.

the / partition and /home should probably be ext4, but ext2/3 wiil work as well. none of these partitions will be available from XP by default. there are drivers to allow XP to use ext systems but I hear they are buggy.

if having XP work with it as well is a high priority, then you will need to leave it unpartitioned for now, and then create the partition from within windows itself. the linux tools never seem to be able to format ntfs so that windows can read it.
I caution you to try to avoid using ntfs regularly in linux, since it has no integration for integrity checks. if you lose power, your ext drives will get a checkup but you would have to remember to reboot into xp to do a chkdsk every time, or that corruption will keep adding up. I find it really hard to maintain an integral ntfs drive in linux if i mount it often. just a caution.

---

### Post by philinux on 2010-06-17
Apart from swap as said above I would go with ext4 for the linux file systems.

[http://arstechnica.com/open-source/news/2009/01/super-fast-ext4-filesystem-arrives-in-ubuntu-9-04.ars](http://arstechnica.com/open-source/news/2009/01/super-fast-ext4-filesystem-arrives-in-ubuntu-9-04.ars)

---

### Post by Sharang.d on 2010-06-18
Can i make a relatively small (say 20gb?) /home [Just for settings, etc] and create another Drive [ext4] to store my actual data?
Forget about the XP partitions for the time being.

---

### Post by jerome1232 on 2010-06-18
> **Sharang.d said:**
> Can i make a relatively small (say 20gb?) /home [Just for settings, etc] and create another Drive [ext4] to store my actual data?
Forget about the XP partitions for the time being.

Yeah that's what I do, I create symlinks for the ~/Videos, ~/Pictures, ~/Documents, ~/Downloads, and ~/Music folders that all point to the data partition.


Ie

```

lrwxrwxrwx  1 jeremy jeremy       19 2010-05-03 07:21 Documents -> /mnt/data/Documents
lrwxrwxrwx  1 jeremy jeremy       19 2010-05-03 07:20 Downloads -> /mnt/data/Downloads
lrwxrwxrwx  1 jeremy jeremy       15 2010-05-03 07:18 Music -> /mnt/data/Music
lrwxrwxrwx  1 jeremy jeremy       18 2010-05-03 07:17 Pictures -> /mnt/data/Pictures
lrwxrwxrwx  1 jeremy jeremy       16 2010-05-03 07:19 Videos -> /mnt/data/Videos

```

---

### Post by Sharang.d on 2010-06-18
> **jerome1232 said:**
> Yeah that's what I do, I create symlinks for the ~/Videos, ~/Pictures, ~/Documents, ~/Downloads, and ~/Music folders that all point to the data partition.


Ie

```

lrwxrwxrwx  1 jeremy jeremy       19 2010-05-03 07:21 Documents -> /mnt/data/Documents
lrwxrwxrwx  1 jeremy jeremy       19 2010-05-03 07:20 Downloads -> /mnt/data/Downloads
lrwxrwxrwx  1 jeremy jeremy       15 2010-05-03 07:18 Music -> /mnt/data/Music
lrwxrwxrwx  1 jeremy jeremy       18 2010-05-03 07:17 Pictures -> /mnt/data/Pictures
lrwxrwxrwx  1 jeremy jeremy       16 2010-05-03 07:19 Videos -> /mnt/data/Videos

```

Yes yes this is what im looking for!
So i have to create a separate /data partition during install like i would do for /home?
Like /home helps restoring settings etc by mounting it again after new install can i even mount my old /data as a new partition to use the old data?

---

### Post by dino99 on 2010-06-18
better to prepare your partitions before installing

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by Sharang.d on 2010-06-18
> **dino99 said:**
> better to prepare your partitions before installing

[http://partedmagic.com/](http://partedmagic.com/)

[QUOTE=http://partedmagic.com/]Parted Magic requires at least a i586 processor[/QUOTE]
I got i386. Will it work? :confused: and yeah i know GParted will work but im asking about this one.

---

### Post by philinux on 2010-06-18
The partitioner part of installer  on the livecd does it for you.

Or you could install gparted from the livecd and prep them first. Makes no difference really.

---

