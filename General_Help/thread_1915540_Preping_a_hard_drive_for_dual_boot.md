---
title: "Preping a hard drive for dual boot?"
date: 2012-01-26
forum: General Help
---

### Post by the lemming on 2012-01-26
Could somebody please advise the best method for preping a hard drive for Ubuntu and Windows 7?

I've got the Window's 7 partition covered and I will have another partition just for data.  My problem is I'm not too sure what to do with the Ubuntu install.

I would very much appreciate advice on sizes of the various partitions and their file structure.  I am especially interested in the size of the swap partition and the file structure, because there are so many to choose from.

Does the Swap File have to be 2.5 times the size of my RAM because 10Gb for a swap seems excessive.  When RAM used to be 128Mb I can see the point but when RAM chips are 2Gb on average is this now considered a good rule-of-thumb?

I'm going to be putting a 750Gb drive into my laptop.

Cheers

---

### Post by Dngrsone on 2012-01-26
If you have >2GB RAM, then I recommend making your swap file the same size as your quantity of RAM.  Of course, someone will rush in and disagree with me, but really Ubuntu shouldn't need to use swap when you have that much RAM available, and the only time I can think that it would be used is maybe for suspend or hibernation.

You really don't have to partition anything extra for a typical Ubuntu install, though many power users will tell you to make a separate partition for /home.

I have 30GB allocated for / (root) and 40GB for my /home partition.  Music and such are on a separate drive/partition.

My / partition does sometimes get full, though, so you might give yours a little more space (with 720GB, you can afford it).

---

### Post by the lemming on 2012-01-26
Hello

Thanks for replying and I have a couple of more questions.

I understand what / (root) is and this is where the operating system is kept but I'm not too sure exactly what /home is.

Is /home just a storage location for my data?
Or is it something more important and necessary for the smooth running of a distro?


If so then I'm after a communal storage area which Windows 7 and Ubuntu can access.

Could you please tell me what file structure I should format for / (root) and /home?

Cheers

---

### Post by Paqman on 2012-01-26
> **the lemming said:**
> 
Is /home just a storage location for my data?


You can put your data there. By default a lot of apps will assume that you want to. But mostly it's used to contain all your individual settings and config files.

> 
If so then I'm after a communal storage area which Windows 7 and Ubuntu can access.


That's not problem. Just create an NTFS partition and dump your files there. Both OSes can read/write to NTFS.

> 
Could you please tell me what file structure I should format for / (root) and /home?


By default the Ubuntu installer will choose Ext4, which is a perfectly good choice.

---

### Post by the lemming on 2012-01-26
> **Paqman said:**
> You can put your data there. By default a lot of apps will assume that you want to. But mostly it's used to contain all your individual settings and config files.



That's not problem. Just create an NTFS partition and dump your files there. Both OSes can read/write to NTFS.



By default the Ubuntu installer will choose Ext4, which is a perfectly good choice.



Thank you, this has ticked all my boxes.

Cheers

---

### Post by Dreamer Fithp Apprentice on 2012-01-26
For what it is worth I've checked system monitor a lot and logs on occasion and I've never seen ANY evidence that swap came into use at all on my desktop with 2 gB RAM. I never hibernate or suspend. If you don't intend to hibernate or suspend and you have enough RAM I think a swap partition is a waste HD space.

Having home on a separate partition probably does make it easier to keep your settings and preferences if you reinstall if you are CAREFUL in reinstalling not to format or overwrite the home partition. I've never done it that way because I've never had so many tweaks and settings that redoing them seemed like much of a bother and making home merely a directory in the root partition gives me more flexible use of the HD space devoted to the system including home. But someone who kept all their data in home, as is quite common, especially for people booting only one OS, would certainly want it on a separate partition. I boot multiple OSes and am frequently reinstalling. I keep my data on separate partitions. The few scripts and images I use to create custom buttons and menus and such I keep in a folder in home that I backup by copying the whole folder to my data partition and then just copy it back when I reinstall.

If you use NTFS for the common data partition bear in mind that the different nature of permissions on NTFS and a native linux (lol, the spell checker here doesn't like "linux"!) filesystem can sometimes cause unexpected problems. You can store a tar there just fine, for instance, but if it is software, you may need to copy it to an extN file system before you extract and use it. I've never tried doing it the other way around and using an extN file system for a common data area. But there are windows programs for accessing extN filesystems and perhaps someone else can comment as to whether there are similar permission problems in Windows using extN systems.

---

### Post by Cavsfan on 2012-01-26
Once you get your dual boot setup correctly, you might want to check out the tutorial in my sig.
It is great for dual booting and having a nice custom screen that you don't have to mess with when a new kernel is installed.
My latest screen that I have is on the last page. I change it around occasionally if I get bored.

Good Luck!:)

---

