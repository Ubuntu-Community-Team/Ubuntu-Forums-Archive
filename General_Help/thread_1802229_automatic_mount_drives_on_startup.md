---
title: "automatic mount drives on startup"
date: 2011-07-11
forum: General Help
---

### Post by Arggg on 2011-07-11
Hello everybody! 

I have just installed Ubuntu 11.04. It is the first time I use something else other than windows and right now I have both Windows XP and Ubuntu installed. My problem here is: 
I have my music database on a "windows disk". Everytime I start my music player Rhythmbox, it is either empty (because the drive was still not mounted) or it fetches for all the music again. My questions are: 

- Would it be possible to solve this problem by automating the mounting of the disk where I have my music at startup? 

- How can I do it? I tried to use this proceeding [http://www.nyutech.com/2009/03/make-ubuntu-mount-partitions-and-drives.html](http://www.nyutech.com/2009/03/make-ubuntu-mount-partitions-and-drives.html) but, although the disk was successfully mounted at startup, my screen keeps going black every 1-5 seconds for 1 second... so I had to undo what I had done... 

Thanks
Arggg

---

### Post by Surendil on 2011-07-11
If i'm not wrong, you should add your music partition to "mtab", that way it will mount it automatically

---

### Post by pqwoerituytrueiwoq on 2011-07-11
i would use fstab and mount it inside /mnt
then i would turn my music folder into a symlink to go to my music on windows
you should not need to chmod/chown anything since it is on a ntfs partition
```
man fstab
```
or google fstab mount windows

---

### Post by Groggster on 2011-07-11
Hello! Now i do not know why that method did not help you, as this is how i am doing it right now without any trouble. Ill post a short guide here, in case you missed something.
Use the following commands in the terminal in the same order as presented:
sudo -i
(state your password)

fdisk -l (find your windows partition. It will likely be named sda1 if you previously had windows and installed Ubuntu on the same physical disk, however it may be named sdb2 or whatever. Look for the ntfs partition that is _not_ 100Mb)

mkdir /media/windows (or replace "windows" with something of your own liking)

gedit /etc/fstab 
Begin typing on the line below the text that is already there, and use [TAB] instead of space. Also use the partition name you got with the fdisk command instead of ***

Type: /dev/*** /media/windows ntfs defaults 0 0

Save and close gedit.

mount -a

And thats it. Keep in mind that you REALLY have to type everything in fstab correctly, otherwise it will not work.

---

### Post by Arggg on 2011-07-14
> **Groggster said:**
> 
Begin typing on the line below the text that is already there, and use [TAB] instead of space. 
And thats it. Keep in mind that you REALLY have to type everything in fstab correctly, otherwise it will not work.

I reviewed what I had done and the problem was that I copied and pasted the lines from the explanation on the website and for the last line one has to use the TAB and not the space. It is now working correctly! :D


> **pqwoerituytrueiwoq said:**
> i would use fstab and mount it inside /mnt
then i would turn my music folder into a symlink to go to my music on windows
you should not need to chmod/chown anything since it is on a ntfs partition


Is there a performance advantage using this method or any other kind of advantage over the procedure I followed?

Thanks for your replies!

---

