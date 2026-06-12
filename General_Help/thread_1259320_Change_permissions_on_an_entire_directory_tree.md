---
title: "Change permissions on an entire directory tree"
date: 2009-09-06
forum: General Help
---

### Post by Johny79 on 2009-09-06
I have all my music on a separate drive from when I used Windows including around 2000 tracks (in various folders) that I recorded from my vinyl/tape collection.

The problem is that having switched to Ubuntu I can't edit any of the files or update their audio info (all say "Unknown", "Unknown Artist" etc at the moment in Rhythmbox) and I'd really like to sort them all out once and for all.

The properties of the files show Root as the owner, and it states "You are not the owner, so you cannot change these permissions".

I searched the forum and came up with this...

[http://www.linuxheadquarters.com/howto/basic/chown.shtml](http://www.linuxheadquarters.com/howto/basic/chown.shtml)

I use...

cd /media/Media

... to change to the relevant drive, and then...

sudo chown <username>.<group> Audio

...to change ownership, but it does nothing. :confused:

I don't get an error or anything, it just doesn't change anything, any ideas on what I'm doing wrong or an easier way to do this??

I should add that the other dozen or so folders on the drive don't have the same issue, plus I can quite happily change the track info through Rythmbox for some files and not others which seems odd to say the least.

I have three copies of the files on my laptop, desktop, and home server, all of which have the same issue, ideally I'd like to get one copy completely sorted out and then just replace the entire directory on the other systems with the "fixed" version.

Any ideas??

---

### Post by hal8000 on 2009-09-06
> **Johny79 said:**
> I have all my music on a separate drive from when I used Windows including around 2000 tracks (in various folders) that I recorded from my vinyl/tape collection.

The problem is that having switched to Ubuntu I can't edit any of the files or update their audio info (all say "Unknown", "Unknown Artist" etc at the moment in Rhythmbox) and I'd really like to sort them all out once and for all.

The properties of the files show Root as the owner, and it states "You are not the owner, so you cannot change these permissions".

I searched the forum and came up with this...

[http://www.linuxheadquarters.com/howto/basic/chown.shtml](http://www.linuxheadquarters.com/howto/basic/chown.shtml)

I use...

cd /media/Media

... to change to the relevant drive, and then...

sudo chown <username>.<group> Audio

...to change ownership, but it does nothing. :confused:

I don't get an error or anything, it just doesn't change anything, any ideas on what I'm doing wrong or an easier way to do this??

I should add that the other dozen or so folders on the drive don't have the same issue, plus I can quite happily change the track info through Rythmbox for some files and not others which seems odd to say the least.

I have three copies of the files on my laptop, desktop, and home server, all of which have the same issue, ideally I'd like to get one copy completely sorted out and then just replace the entire directory on the other systems with the "fixed" version.

Any ideas??



You're making a small mistake in your command, it should be
cd /media/Media
sudo chown user:user *

The * changes the permissions of all files in the Media directory, you dont have to change group to audio just your regular user name, so replace user with your username that you created.
If unsure run
ls -l

from your home directory.
Hope that helps

---

### Post by Johny79 on 2009-09-06
> **hal8000 said:**
> You're making a small mistake in your command, it should be
cd /media/Media
sudo chown user:user *

The * changes the permissions of all files in the Media directory, you dont have to change group to audio just your regular user name, so replace user with your username that you created.
If unsure run
ls -l

from your home directory.
Hope that helps

Thanks for that, I'm still not having any luck though.

I confirmed the username & group with ls -l on my home directory just to be 100% sure, but the chown command still does nothing, again there's no errors or anything either.

---

### Post by Johny79 on 2009-09-06
Also it occurred to me that surely I should be able to use...

gksudo nautilus

... and then use the folders properties window to change the permissions?

For some reason though it just reverts to what it was set to originally more as less as soon as I try and change it.

**EDIT:** Oh crap, I just realized that ALL the files on that drive now have the same issue and are set to root as the owner, the exact opposite of what I wanted :rolleyes:

---

### Post by jack_hmr on 2009-09-06
Do not CD to the directory first and try this:
```
sudo chown -R username:username /media/Media
```

---

### Post by Johny79 on 2009-09-06
> **jack_hmr said:**
> Do not CD to the directory first and try this:
```
sudo chown -R username:username /media/Media
```

Thanks but same thing, pauses for a few seconds like it's doing something, no errors, but the owner/permissions are unchanged. :(

---

### Post by jack_hmr on 2009-09-06
Can you post everything from the terminal when trying the last two methods?

---

### Post by Johny79 on 2009-09-06
Ok so I just came across this thread...

[http://ubuntuforums.org/showthread.php?p=7844810](http://ubuntuforums.org/showthread.php?p=7844810)

Now the 2nd post sounds very similar to the problems I'm having so do I need to change the way I'm mounting the drive to fix the problem?

I'm still fairly new to Linux so if anyone has some more info on this it would be helpful.

---

### Post by Johny79 on 2009-09-06
> **jack_hmr said:**
> Can you post everything from the terminal when trying the last two methods?

Looks like we posted at the same time, bear with me a second and I'll grab that for you...

> 
john@<system>:~$ sudo chown -R john:john /media/Media
john@<system>:~$ 


> 
john@<system>:~$ cd /media/Media
john@<system>:/media/Media$ sudo chown john:john *
john@<system>:~$ 


Also in case it's relevant...

> 
john@<system>:/media/Media$ ls -l /media
total 36
lrwxrwxrwx 1 root root     6 2008-11-22 10:02 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2008-11-22 10:02 cdrom0
drwxrwxrwx 1 root root 20480 2009-08-31 13:14 disk
drwxrwxrwx 1 root root  4096 2009-09-06 13:28 Media
drwxrwxrwx 1 root root  4096 2009-09-04 16:40 SafeStore
drwxrwxrwx 1 root root  4096 2009-09-02 12:07 Store
john@<system>:/media/Media$ 

> john@<system>:~$ ls -l
total 139488
drwxr-xr-x  2 john john     4096 2009-09-02 12:26 Desktop
drwxr-xr-x  2 john john     4096 2008-11-23 10:42 Documents
lrwxrwxrwx  1 john john       26 2008-11-22 10:08 Examples -> /usr/share/example-content
drwxr-xr-x  2 john john     4096 2009-08-28 17:05 mp3tmp
drwxr-xr-x  3 john john     4096 2009-08-31 14:14 Music
drwxr-xr-x  4 john john     4096 2009-09-02 12:06 Pictures
drwxr-xr-x  2 john john     4096 2008-11-23 10:42 Public
drwxr-xr-x  2 john john     4096 2008-11-23 10:42 Templates
drwxr-xr-x  2 john john     4096 2008-11-23 10:42 Videos
-rw-r--r--  1 john john 56131207 2009-08-31 15:01 wormux-0.8.4-static-x86.sh
john@<system>:~$ 

---

### Post by jack_hmr on 2009-09-06
I haven't had trouble with permissions on an NTFS partion before but that could be the issue.

Please run this in the terminal
```
gksu gedit /etc/fstab
```
and post the code and comment for the drive in question or just post the entire thing.

---

### Post by Johny79 on 2009-09-06
Here you go...

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=c574a577-336f-412a-8fc6-4d31fa114032 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=99dd228f-f392-43a5-bfc1-4f43ab053fc3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

The other drives (including "Media") aren't mounted at boot I just mount them using the "Disk Mounter 2.26.1" Applet from my top panel as and when I need them.

Tried installing the ntfs-config tool to see if it would help and enabled automatic mounting, so it now looks like this...

> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb2 :
UUID=c574a577-336f-412a-8fc6-4d31fa114032 / ext2 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb3 :
UUID=99dd228f-f392-43a5-bfc1-4f43ab053fc3 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb4 /media/SafeStore ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda2 /media/Store ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda1 /media/Media ntfs-3g defaults,locale=en_GB.UTF-8 0 0

Hasn't made a difference.

---

### Post by jack_hmr on 2009-09-06
Lets try mounting it in your home folder to see if it will change the permissions.

If you don't already have a folder named test (if you do use another name), in the terminal
```
sudo mkdir /home/test
```
to create an empty folder named test.

In the terminal
```
sudo umount /media/Media
```
to unmount the drive.

Then
```
sudo mount /dev/sda1 /home/test
```
to mount as the test folder.

See if the permission are changed or are changeable.

---

### Post by Johny79 on 2009-09-06
Cool, I didn't even realize that was possible! :)

Mounted like that I can now edit the files, set track names etc etc, BUT I still can't change the actual file/folder permissions.

Still it's good progress as at least I now have a way of sorting out all the track info even if I can't fix the permissions, so thanks!

Any idea why this would be the case though as I'm now even more confused, lol :D

---

### Post by jack_hmr on 2009-09-06
Basically the user can do whatever it wants to stuff in the home folder.
[https://help.ubuntu.com/community/HomeFolder]("https://help.ubuntu.com/community/HomeFolder")

To make it permanent:
Get the fstab set up how you want it (mount on boot or automatically) using the ntfs-config tool.

**Save a copy of fstab in case there is a typo.**

Create a folder in the home directory with a better name than "test".

In the original fstab change the mount location from /media/Media to /home/test (replace "test" with the new folder you created.

Save fstab

To test it run in the terminal
```
sudo umount /home/test
```
```
sudo mount -a
```
This mounts everything as instructed by fstab.

If you don't get any errors and the drive is mounted in the new location you are good to go. If there are errors you can post back for help but they must be fixed or the fstab replaced with the backup file before you reboot.

---

### Post by Johny79 on 2009-09-06
Just tried it out and it works great so thanks again! :D

Time to start going through all those tracks completing the info, will be nice to have it all done at last. :)

---

