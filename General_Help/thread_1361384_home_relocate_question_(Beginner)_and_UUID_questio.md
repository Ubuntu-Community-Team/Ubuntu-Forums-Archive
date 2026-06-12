---
title: "/home relocate question (Beginner) and UUID question (two parter)"
date: 2009-12-21
forum: General Help
---

### Post by esmurdo on 2009-12-21
I'd like to prefix this post by saying that I have tried searching for an answer to this dilemma, but so far the internet I'm using while deployed is being too finicky for me to continue this fruitless search.


I have reformatted my HP laptop with Ubuntu 9.10 as ext4 on my 250gb HD. I have another internal 320gb HD that has my media from an old Windows (blech) install that is formatted ntfs.

My /etc/fstab layout:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=52830052-e945-4f67-8e42-863d37db7bd3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=7f9f87ba-fe52-4c79-9c30-2e1607bcd37f /home           ext4    defaults        0       2
# /windows was on /dev/sdb1 during installation
UUID=A43E55723E553F0C /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda1 during installation
UUID=80420744-3c1f-4f52-8833-87f7a5a72090 none            swap    sw              0       0
```

My first question is how do I lookup the UUID reference lines?

My second, and main question is a little bit more involved. As I mentioned, I have all of my movies, pictures, documents, music, etc on the legacy HD that is currently mounted at /windows from the installation. I would like to have the Documents, Music, etc folders in my current /home directory link directly to their counterparts on the other hard drive. How do I do this?

I would prefer to keep my /home directory on the install hard drive, as it is my understanding (correct me if I'm wrong) that programs and such are installed under your /home directory. I wish to keep programs and settings under the 250gb HD, and keep all media on the 320gb HD for future use and upgrades.

Any and all help is appreciated on this matter!

---

### Post by oldfred on 2009-12-22
sudo blkid

I mount my NTFS shared partition directly into /home. When I did my brand new clean install of Karmic I moved all my data from ubuntu into a data partition and linked that data into my /home. I do not know if you can link NTFS directories.

My fstab 
# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  
# Entry for /dev/sda2 :
UUID=13a684e4-2849-4566-9528-21cd07028a9a  /media/backup  ext3         auto,users,rw,relatime               0  2  
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

I deleted the empty new directories in /home and created these:
ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents
ln -s /usr/local/fred/data/Pictures
ln -s /usr/local/fred/data/Videos

Programs are not actually installed in /home but all your personal settings are in hidden files and directories in /home.

---

### Post by turvyc on 2009-12-22
About the UUID question, well, I'm not sure if this is what you're looking for, but you can look up the UUIDs of your drives/partitions by opening a terminal and using the command:
```
blkid
```
Hope this helps!

---

