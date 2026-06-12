---
title: "Expanding Home directory"
date: 2010-10-23
forum: General Help
---

### Post by Torqumada286 on 2010-10-23
I managed to get my new install of 10.10 to use my old /home directory on another drive that had my original 10.4 install on it.  However, my system is only using a fraction of the old drive that /home is on.  Is there anyway to get it to use the entire drive as /home to give me more space to work with?

Torquamda

---

### Post by 3Miro on 2010-10-23
What do you mean only a fraction? Can you go to terminal and tell us what t he comands
```
 sudo fdisk -l 
```
and
```
 df 
```
return?

There is no reason why you would be restricted to only a portion of your folder.

---

### Post by Torqumada286 on 2010-10-23
The rest of the old drive still has the old 10.4 system files on it and it says it only has about 15% of a 320gb drive available for use as /home.  Some of that room must be taken up by the system files.  I can't seem to access the drive directly to remove those system files to make extra room for the /home directory.

Relevant output of those commands:

> 
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2add431d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37434   300688573+  83  Linux
/dev/sdb2           37435       38913    11880037    5  Extended
/dev/sdb5           37435       38913    11880036   82  Linux swap / Solaris


> 
/dev/sdc1            469021168  22127736 423068488   5% /
none                   1986128       316   1985812   1% /dev
none                   2028724       336   2028388   1% /dev/shm
none                   2028724       212   2028512   1% /var/run
none                   2028724         0   2028724   0% /var/lock
/dev/sdb1            295968836 236392324  44542084  85% /home
/home/james/.Private 295968836 236392324  44542084  85% /home/james
/dev/sdf5             11880032     60212  11819820   1% /media/New Volume
/dev/sdd1            488264736 302070656 186194080  62% /media/My Book
/dev/sdf1            300688572 118879040 181809532  40% /media/Back up 2
/dev/sde1            488384508 474300956  14083552  98% /media/Back up 1


Torqumada

---

### Post by 3Miro on 2010-10-23
```
 /dev/sdb1 295968836 236392324 44542084 85% /home 
```
236GB is too much to be taken just by the remainder of the other system (you have to work really hard to get the system part of Ubuntu above 20GB). What did you do to mount the disk and are you sure you have not taken up all the space with your files (like home movies, lots of mp3 files, installations of wine games and other large things).

Can you describe what you did. There may be an issue with a quota set, however, I don't know much about those (try "sudo df" to see if you get the same result, if so, then try to describe what you did to make it take your old home folder).

---

### Post by Torqumada286 on 2010-10-23
I did a full install of 10.10 on a new drive and during the process, designated my old drive as the home drive.  I am planning on moving and deleting some files, I just didn't think I had that much on the drive.

Torqumada

---

### Post by 3Miro on 2010-10-23
In the old install, did you have the entire system or just your home folder on that drive? If you go to nautilus and look into /home (not your home, your home is /home/your_username, look at /home only). Does it contain a bunch of folders like /usr, /root and so on. If so, then you do have some garbage there (though it is probably not much). You can check to see if any one of those folders is excessively large (the entire thing, even if it is there, should be no more than 20GB).

---

### Post by Torqumada286 on 2010-10-23
> **3Miro said:**
> In the old install, did you have the entire system or just your home folder on that drive? If you go to nautilus and look into /home (not your home, your home is /home/your_username, look at /home only). Does it contain a bunch of folders like /usr, /root and so on. If so, then you do have some garbage there (though it is probably not much). You can check to see if any one of those folders is excessively large (the entire thing, even if it is there, should be no more than 20GB).

Here is what it looks like:

[img]http://666kb.com/i/bns1gsdjdo03smugw.jpg[/img]

The second home listed there actually leads to the files from my old drive.  Everything was on a single drive.

Torqumada

---

### Post by 3Miro on 2010-10-23
I see what is happening.

On a clean install with one partition, you will have system folders like /bin, /usr, /lib and user folders /home/user_joe, /home/user_jane and so on.

On a clean install with two partition where one is / and one is /home, the / partition will have things like bin, usr boot and the /home partition will have user_joe, user_jane ...

In your case, you have an install with bin and usr on one partition and your_user_name on another. However, you also have the old folders from 10.04. What was /bin under 10.04 is now /home/bin, /usr is now /home/usr and so on. That is why you have /home/home/your_old_stuff.

You should clean this up. First move all of your old stuff to your new home folder (or at least the stuff that you need). At this point, you probably don't want to move the dot-foders unless it is something like .mozilla or .thunderbird, which will overwrite your new settings with your old ones (if you had old e-mails or old bookmarks that you want to keep). Then you should make sure you don't have anything useful in the other folders. Normally you are not supposed to be saving thins in the system folders (/bin, /usr and so on). If you haven't saved anything useful there, then you should just delete them. You can do that by going into the terminal and typing
```
 gksudo nautilus 
```

BE VERY CAREFUL. This will give you an instance of the file browser with super-user privileges. You can very, very easily destroy important files. Make sure that everything that you delete is of the form /home/<something> and that <something> is NOT your username.

Or you can use the terminal with:
```

sudo rm -fr /home/bin
sudo rm -fr /home/usr
sudo rm -fr /home/boot
sudo rm -fr /home/etc
sudo rm -fr /home/home
sudo rm -fr /home/initrd
sudo rm -fr /home/sys
sudo rm -fr /home/srv
sudo rm -fr /home/opt
sudo rm -fr /home/lib
sudo rm -fr /home/lib32
sudo rm -fr /home/media
sudo rm -fr /home/mnt
sudo rm -fr /home/proc
sudo rm -fr /home/root
sudo rm -fr /home/dev
sudo rm -fr /home/sbin
sudo rm -fr /home/selinux
sudo rm -fr /home/rmp
sudo rm -fr /home/car

```

Again BE VERY CAREFUL. Make sure you don't have anything useful left, especially in /home/home. Also make sure you copy the commands (and double-check what I have done). If you mess /home/bin with /bin you will permanently damage your system and then you will have to reinstall everything.

---

