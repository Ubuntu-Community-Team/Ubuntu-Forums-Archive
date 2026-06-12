---
title: "Installation"
date: 2011-03-21
forum: General Help
---

### Post by Miykel on 2011-03-21
[FONT=Georgia][SIZE=2]G'Day;  Have a major problem, Desperatley need help Please,[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]    Started to install Ubuntu , got around the partition ok but then I had to add... and the dropdown menu ( can't remember what it's called) gave me options like  \  \Home  \root etc.  etc., Which one is the best for duel boot with W7 64bit.    :confused:[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]Kind regards Miykel[/SIZE][/FONT]

---

### Post by nothingspecial on 2011-03-21
If you want Ubuntu in a single partition you will want to give it a mountpoint of /

If you are manually partition you might want a swap partition of twice the size of your ram, or you can create a swap file later.

---

### Post by An Sanct on 2011-03-21
As far as I remember, I choose "/" as sda, so root was there and could continue with the installation. But it was a long time ago :)

---

### Post by Miykel on 2011-03-21
[FONT=Georgia][SIZE=2]G'Day and thanks so much guys, I'll have another go and use   /  it can only be wrong  (lol)[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]       My PC has 8 gig of ram, W764bit but the partition is 100Gig so I have lots of room.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]   Kind regards  Miykel   :P[/SIZE][/FONT]

---

### Post by MARP1961 on 2011-03-21
If you go for the manual partitioning, just make sure you don't format or alter your ntfs (Windows) partition by accident! If you are feeling more adventurous then give yourself a '/Home' partition also. This will separate your personal settings and data from the system files. If in the future you wish to reinstall Ubuntu this option allows you to keep your data files and settings undisturbed. On your partitioning table allow about 15GB for the Ubuntu system on a '/' ext4 journalling file system, then create as large a '/Home' ext4 journalling partition as you can afford for your separate Home Partition. Set a Swap partition for around 1 and a half times the RAM size on your computer. Make backups of all important files first and go careful with Windows if you wish to keep it.

---

### Post by Topsiho on 2011-03-21
The replies are OK, but I want to make you understand things better (having been a teacher, I never get over this itch for explaining things :)  )

The mount points /, /home, and the swap partition are for the following partitions:

/  is for the root partition, and contains all the system files, assuming you don't use other partitions except:

/home for all files that are owned by the users of the system (documents, pictures, personal configurations, you name it), which you really want to retain when reinstalling a next version of Linux or Ubuntu, and

a swap file, which is kind of extra memory for your computer when this is needed, and should be around twice your RAM (working memory).

Hope this helps you choosing mount points next time without guessing.

The sizes that you need are around 6 GiB (or more, if you install really a lot of applications, or so), for /  , for swap I already told you, and the rest is for /home.
If /home is too small, depending on what personal files you are going to put into it: documents, pictures, movies, then you should make / a little smaller then the 6 GiB I mentioned, but not much smaller.

One other, different, but related point: a hard disk can never contain more than 4 primary partitions.
So if necessary you use logical partitions instead, which will be put into an extended partition (***which itself is one of the 4 primary partitions***), but the Ubuntu installer will take care of that automatically :) if you choose logical partition in stead of primary.


Topsiho

---

