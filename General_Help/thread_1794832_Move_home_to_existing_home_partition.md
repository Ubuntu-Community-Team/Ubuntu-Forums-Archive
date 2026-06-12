---
title: "Move /home to existing /home partition?"
date: 2011-07-01
forum: General Help
---

### Post by Bucky Ball on 2011-07-01
Hi all,

Been digging around and not finding anything that quite works.

Background: I had an existing 10.10 install and 10.04 on another partition. When I installed the 10.04 I told it to use the existing /home partition which is also being used by the 10.10 install. All good, both users have directories with all their data in the same /home partition.

Issue: So, as the 10.04 was 32bit (experimenting but another story) I decided I would replace with 10.04 64bit. All went well except when I did the manual partitioning I screwed up and instead of setting the existing /home partition to 'use but don't format' - which I think is what I must have done last time - I left it as 'don't use and don't format'. So, obviously, now the new 10.04 install has its /home inside /, which I don't want. I want it on the existing /home partition as it was with the previous 10.04 install.

Question(s): Is there any simple(ish) way of doing this without a reinstall? Not a major problem as I have only just installed and can do it again without losing anything but time, but I would like to figure out a way to do it without if possible.

A little more detail:

/media/home = existing /home partition;

I want to essentially move the /home/user directory (rather than the /home) and make it /media/home/user inside the existing partition. Seems easy enough on the surface but becomes involved as I investigate.

Ubuntu 10.04 minimal install with Xfce DE. All tips appreciated. ;)

---

### Post by Bucky Ball on 2011-07-01
As the contents of /home/user is what I want to move to /media/home I could try this:

```
# cp -a /home/user/* /media/home/user
```Then setup /etc/fstab to mount /media/home. At the moment I only have / and /swap:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=d015570f-cd27-4a23-8db7-3eb4d685b48d /               ext4    errors=remoun$
# swap was on /dev/sdb7 during installation
UUID=63d86782-bff4-41c1-924f-37d093fbe371 none            swap    sw           $

```

A little dirty but could work. Would mean I ignore the /home (or delete it) inside / but would need to change the default folder for file manager.

---

### Post by oldfred on 2011-07-01
You have done most of a standard move /home to a separate partition. It may be just adding the partition to fstab, but review the process to see if another step or two is required.

These are all really the same, just using different copy commands.

Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Bucky Ball on 2011-07-01
Oldfred, cheers; just looking at it: wondering if I could: 

* change the fstab to mount /media/home, 
* change the default location of /home to /media/home/user (if I change it to just /media/home it may wipe the /home of the 10.10 user which lives in there also - not killing what's in the original /home partition is the concern else this would be easy).
* how would I change the default location? I've discovered how to do it for a new user, but not for super-user.

Hope that makes sense. I'll check out those links.

* Not exactly but this is what I'm after:

[http://www.cyberciti.biz/faq/howto-change-default-home-directory/](http://www.cyberciti.biz/faq/howto-change-default-home-directory/)

Then I could copy all files over and change pointer, to put it simply ...

From ~/.config/user-dirs.dirs I have: 

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
#
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```Could I copy my files to /media/home/user then change these to, say:

```
XDG_VIDEOS_DIR="$/media/home/user/Videos"
```? Or does this file only affect *other* users, not original?

---

### Post by Bucky Ball on 2011-07-01
Boot into 10.10, copy all files from /home/user in the 10.04 install to the /home partition, boot back into 10.04 and fix the fstab, reboot and point to the folder in /home.

Trouble with this: when booted to 10.04 the /home partition needs to be mounted in /media/home, naturally. Complicates things.

Might get a bit of shut eye, get up and reinstall. ;)

---

### Post by oldfred on 2011-07-01
I have not modified ~/.config/user-dirs.dirs, other than once, I had an error where a folder was under /desktop. Not sure how I did that.

I prefer to leave /home in / (root). It is tiny with only hidden files & folders. Mine is up to 1GB but 3/4 is .wine. I prefer to use another partition for /data and link all the old folders from my original /home like Music, Documents, etc back into /home so it looks like a normal install. Just all my own data is in another partition. I consider this more advanced. And some think it is more windows like. But I want each operating system to have all files (including user settings) on one drive, so it boots correctly without any other drive. Then my data is on another drive (depending on which system I boot). I link same data into many installs so I have all the same files & folders where ever I am.

---

### Post by Bucky Ball on 2011-07-01
Oldfred, exactly what I've been trying to do! How do you change the paths in Xfce? I can't figure out which file to tweak, though I've been looking. Changed ~/.config/user-dirs.dirs but didn't seem to make any difference and when I checked it seemed to be back to what it was, minus my changes (may have re-written on restart).

How do you think I can do this? I remember it being reasonably straight forward with Gnome.

---

### Post by Bucky Ball on 2011-07-01
Well, I tried editing that line from ~/.config/user-dirs.dirs to this:

```
XDG_VIDEOS_DIR="/mnt/home/user/Videos"
```... then this:

```
XDG_VIDEOS_DIR="$HOME/mnt/home/user/Videos"
```... and both times, after a reboot, the line had changed to:

```
XDG_VIDEOS_DIR="$HOME/"
```?

---

### Post by oldfred on 2011-07-01
I mount my /data partition in /mnt and link every folder back. I ended up with this as I was changing from 32bit to 64 and thought I wanted a separate /home. I bought a new larger drive and copied my /home over, but I soon decided I really did not want /home separate but just my data. After doing it a couple of times in new installs I converted it ot a bash script by listing my history I editing a little into a script.

sudo mkdir /mnt/data
sudo chown -R $USER:$USER /mnt/data
sudo chmod -R 766 /mnt/data
#Edit fstab with your UUID:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/$USER
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

Shared /data -see post #4 oldfred
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

