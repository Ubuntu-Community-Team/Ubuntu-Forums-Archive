---
title: "Changing /home partion to NTFS"
date: 2011-04-26
forum: General Help
---

### Post by OldTimeyJunk on 2011-04-26
I'm having some trouble and I though I'd come here before I mess up.

I currently use Ubuntu 10.04.2 LTS and Windows 7 on my laptop. See, Ubuntu can open NTFS partitions but Windows cannot open EXT2 (or any other except NTFS, vFAT etc.) partitions. When I installed Ubuntu I assigned a seperate /home partition, now I realize my mistake. So, now I want to change /home from EXT to NTFS. I know how to format it, but is that it. Do I need to configure some other settings (like fstab) to get it to work?

Please Help (before a fu ... I mean, mess up!)

EDIT: I did find something like this on Whirlpool, it said there was issues with privileges but I don't really care about any of that. Don't give me issues, 'cause I know about them. Just explain how to accomplish this properly!

Thanks,
  Josh

----
I love :popcorn:, no I don't really, I just really like that smiley :)

---

### Post by Elfy on 2011-04-26
Linux and windows approach permissions differently.

Leave the /home as a linux partition.

If you want to have data available to both OS then make a new data partition, format it to ntfs and allow linux access to it.

---

### Post by OldTimeyJunk on 2011-04-26
No, I said - don't give me issues!!! Just someone explain how I could do this. Anyway, I have another Linux system on a HDD (it's been on for quite a while) and it's on an NTFS partition. And, I cannot create another partition because all of mine are Primary and I've had pretty bad experiences with Logical & Extended partitions.

---

### Post by OldTimeyJunk on 2011-04-26
Ok then, what about FAT32?

---

### Post by dragonfly41 on 2011-04-26
Might samba be a compromise ??

[http://www.liberiangeek.net/2010/05/share-filesfolders-between-windows-xp-vista-7-and-ubuntu-10-04-lucid-lynx-via-samba/](http://www.liberiangeek.net/2010/05/share-filesfolders-between-windows-xp-vista-7-and-ubuntu-10-04-lucid-lynx-via-samba/)

...

Sorry .. belay that idea it is for two computers.

You can however read ext3/ext4 partition from Windows .. with the appropriate app.  .. here .. 

[http://stream-recorder.com/forum/access-ext2-ext3-ext4-partitions-windows-t6291.html](http://stream-recorder.com/forum/access-ext2-ext3-ext4-partitions-windows-t6291.html)

---

### Post by tgm4883 on 2011-04-26
Hmm, where to start.


You mention that you had bad experience with extended partitions. I'd venture you are doing it wrong then. Extended partitions are pretty common.

You can't use NTFS or FAT* as your home partition. You Linux system wouldn't work properly because the permissions couldn't be set correctly.

You should probably format it ext3 and load the ext driver for windows  [http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html](http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html)

---

### Post by coffeecat on 2011-04-26
> **OldTimeyJunk said:**
> No, I said - don't give me issues!!!

forestpixie was not giving you issues. You cannot have a home partition formatted NTFS because NTFS doesn't support Linux permissions.

> **OldTimeyJunk said:**
> Ok then, what about FAT32?

Nor does FAT32. You cannot use Microsoft filesystems for home partitions. These are not "issues"; they are facts. The only way to do what you want is to create another partition formatted NTFS (or FAT32) for data to be shared by both OSs. If that means learning how to cope with logical partitions, then that's unavoidable. If you need help with this, there are plenty of people willing to do so. It's not as bad as it might seem. :)

---

### Post by OldTimeyJunk on 2011-04-26
Linux support NTFS. I can still access my Windows partitions and as I said I have a Linux OS on another HDD with NTFS.
And, I don't use Samba.
Fine, I'll figure it out myself. Since none of you are actually giving me answers, all your doing is telling me not to do it!

---

### Post by OldTimeyJunk on 2011-04-26
> **tgm4883 said:**
> Hmm, where to start.


You mention that you had bad experience with extended partitions. I'd venture you are doing it wrong then. Extended partitions are pretty common.

You can't use NTFS or FAT* as your home partition. You Linux system wouldn't work properly because the permissions couldn't be set correctly.

You should probably format it ext3 and load the ext driver for windows  [http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html](http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html)

Hmm, sorry, must have overlooked your post.
First, I havn't been doing the Extended partitions thing wrong, what it was that when I was making Extended partitions it left a 2MB space between partitions leading me to accidentally formatting the wrong partition (I figured I could use a 2MB space to install Kolibri onto).
Secondly, I couldn't care less about premissions.
Thirdly, YOU HAVE ACTUALLY HELPED ME :). I'll use that driver. Thanks!

---

### Post by ~Plue on 2011-04-26
> **OldTimeyJunk said:**
> Linux support NTFS. I can still access my Windows partitions and as I said I have a Linux OS on another HDD with NTFS0
none of them were telling you that linux cant read ntfs, they were saying ntfs handles file permissions differently.
the closest the you could come to using an ntfs partition as /home would be using symbolic links in your home directory to files on another ntfs partition.. or you could use the driver tgm4883 linked to to read the partition from windows

---

### Post by kaldor on 2011-04-26
It helps to listen to instructions instead of telling people they're giving you issues.

Make a new partition with whatever size you like. Format it as NTFS. Give Linux permission to access it. Same with Windows. Now, you have a shared partition for your files.

Edit: Just noticed your "none of them were giving me answers, just telling me not to do it" part. You asked for help, you refused, and that's all these forums can do.

---

### Post by coffeecat on 2011-04-26
> **~Plue said:**
> or you could use the driver tgm4883 linked to to read the partition from windows

Which, unfortunately, doesn't work with...

a - ext4 filesystems, and...

b - ext3 filesystems with 256-byte inodes, which has been the default in mke2fs and Gparted for at least a couple of years.

I predict the OP will be back demanding answers and no "issues".

---

### Post by tgm4883 on 2011-04-26
> **OldTimeyJunk said:**
> Hmm, sorry, must have overlooked your post.
First, I havn't been doing the Extended partitions thing wrong, what it was that when I was making Extended partitions it left a 2MB space between partitions leading me to accidentally formatting the wrong partition (I figured I could use a 2MB space to install Kolibri onto).
Secondly, I couldn't care less about premissions.
Thirdly, YOU HAVE ACTUALLY HELPED ME :). I'll use that driver. Thanks!

We know you don't care about permissions. That's not what we are talking about though. Linux cares about permissions, especially in the home directory. If you formatted your home directory as NTFS, the machine would boot, but likely wouldn't be able to log you in.

---

### Post by ~Plue on 2011-04-26
> **coffeecat said:**
> Which, unfortunately, doesn't work with...
a - ext4 filesystems, and...
b - ext3 filesystems with 256-byte inodes, which has been the default in mke2fs and Gparted for at least a couple of years.

I predict the OP will be back demanding answers and no "issues".
Oh, how about the ext2fsd driver? does it still work?

---

### Post by trollger on 2011-04-26
If you really want to do this and im not sure why you would then you need to install gpated. create a new partion and call it home, format it to ntsf and move the files from your home folder to it. I have never tried this before but you should be able to make a symbolic link from the home partion in you media directory to where your home folder normaly would be.

---

### Post by coffeecat on 2011-04-26
> **~Plue said:**
> Oh, how about the ext2fsd driver? does it still work?

I don't know. I used the ext2ifs driver for a while before 256-byte inodes became the norm. The other thing I wasn't happy about it was that it granted you full read-write acess to **everything**, including system files! :-s

According to its website:

[http://www.ext2fsd.com/?page_id=2](http://www.ext2fsd.com/?page_id=2)

... ext2fsd is still alive and doesn't have some of the drawbacks of the ext2ifs driver. But I wouldn't use it. I much prefer to have a shared NTFS data partition where I have Windows. But, seemingly, this is not an option the OP is prepared to consider.

---

### Post by bodhi.zazen on 2011-04-26
> **trollger said:**
> If you really want to do this and im not sure why you would then you need to install gpated. create a new partion and call it home, format it to ntsf and move the files from your home folder to it. I have never tried this before but you should be able to make a symbolic link from the home partion in you media directory to where your home folder normaly would be.

As has been pointed out many times in this thread, although Linux can read / write to ntfs partitions, you can not use a fat or ntfs partition as a /home partition.

This is because neither fat or ntfs support linux permissions. When you mount one of these partitions, as a part of the mount process, directories and files are assigned permissions, but they are all the same. All files and directories will be owned by the same user. All files will have the same permissions. All directories will have the same permissions.

This will break many of the functions of various configuration files in your home directory.

Links do not help as they do not fix the permissions problem.

Best to use NTFS as a separate /data partition with links to sub directories in home.

so ..

ln -s /media/data/music /home/your_user/music
ln -s /media/data/documents /home/your_user/documents


etc

With that said, there are reports of people using ntfs with the ntfs-3g driver on a single user system.

Use the "windows_names" option

> windows_names
	This option prevents files, directories and extended attributes to be created with a name not allowed by windows, either because it contains some not allowed character (which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) or because the last character is a space or a dot. Existing such files can still be read (and renamed).

For details see : [http://www.tuxera.com/community/ntfs-3g-manual/](http://www.tuxera.com/community/ntfs-3g-manual/)

Note: That method will not work on a multi user system and it may break various features such as ssh, gpg, or even X (your gui).

Best of luck to you =)

---

### Post by OldTimeyJunk on 2011-04-29
Sorry for being so rude everyone. I can see what you've been telling me. The Ext2 driver thing works fine. I'm happy now!

---

### Post by jmore9 on 2011-04-29
Here is an example of what i have done on one of my machines ( the slowest one ).

Hda has : PATA drive 160 gig

partition 1 as EXT4 and I am lazy so everything is dumped into /

partition 2 swap

partition 5 NTFS manually mounted as needed

Hdb has : PATA drive 320 gig

partition 1 as NTFS manually mounted as needed

partition 2 as NTFS manually mounted as needed

HDc has : SATA 500gig

partition 1 as NTFS manually mounted as needed

All the NTFS drives are left overs from Winxp Pro install.  To much to move at once so just left them and use them as until cleaned out.  Using 1010 ubuntu and no problems at all.

Winxp used to be where ext4 and swap are.

You can also get a copy of Gparted Live and burn that to cd .   Thats what i use with everything when switching.

---

### Post by Elfy on 2011-04-29
> **OldTimeyJunk said:**
> Sorry for being so rude everyone. I can see what you've been telling me. The Ext2 driver thing works fine. I'm happy now!

Welcome.

Be careful with it.

---

