---
title: "How do I copy a hard drive from command line?"
date: 2011-05-04
forum: General Help
---

### Post by emmiesix on 2011-05-04
Ubuntu is getting stuck at the loading screen after an aborted attempt to upgrade to 11.04.  It's my own fault - the install was running out of room on /, and I, like an idiot, decided to delete some package files under /var/something/archive, thinking they were "old"... I quickly realized they were in fact the new packages being installed... anyway after killing the thing and rebooting it is pretty damn broken (mostly because I can't get networking going so running in dpkg repair mode doesn't do much because, well, I deleted the packages).

I want to copy all the files off my /home and other meaningful partitions onto an external drive so I can just do a clean install.  I can actually login to the command line under recovery mode, but I can't get the GUI started.  I know it's possible to copy the contents of the partitions to an external, but I don't know the commands... can anyone help?  I really, really, really don't want to screw this up.

---

### Post by oldfred on 2011-05-05
You  have to have a partition to put data into, create a mount point, mount partition to mount point & copy data to new partition.

You also may be able to use liveCD to chroot into your system and update it from the chroot.

these commands are part of my normal backup script, adjust to suit. My /mnt/data is really my data partition, but I link folders into /home. But I have lots of links in /home and my regular backup would have too much data if I backed up everthing, so I just backup some critical data (all of /home's hidden settings & Documents folder) with this script. The l parameter is so I do not follow links in /home.

mkdir /mnt/Backup
mount -t ext3 /dev/sda2 /mnt/Backup
rsync -aruvlP /mnt/data/Documents /mnt/Backup
rsync -aurvlP /home /mnt/Backup

You probably do not need to reinstall grub, but good instructions on chroot. I like kansas as he has combined lines into one line to copy & paste.
drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
kansasnoob- full chroot one line version with &&----
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Then update system once chrooted.

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by emmiesix on 2011-05-05
Thanks oldfred!

So, I may be able to chroot into the local system from my live-usb, and update from there, without doing all the file transfers, is that what you mean?  That would be great, because I have about 400 GB (mostly stuff in a data partition, plus ~ 40 GB in my /home).

When I installed ubuntu on this machine I went a little overboard on the partitions.  /home, /usr, /media/shared (data), and several others were given their own partitions.

From a live-usb, I used gparted and some posts from a previous screw-up to figure out my partition list:

/dev/sda1 /

/dev/sda2 -- subpartitioned into sda5 - sda10:
/dev/sda10 swap
/dev/sda5 /usr
/dev/sda6 /tmp -- > not used?
/dev/sda7 /boot
/dev/sda8 /opt
/dev/sda9 /root

/dev/sda3 /home
/dev/sda4 /media/shared

So the idea would be the following:

sudo -i
mount /dev/sda1 /mnt
mount --bind /dev  /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys  /mnt/sys
mount --bind /usr/ /mnt/usr

and then chroot, etc.

Now I ran the first mount command to mount sda1, but I am a bit unsure because /usr and /boot are on their own partitions. Shouldn't I mount them into /mnt/usr and /mnt/boot directly instead of doing the bind command?

Strangely, in exploring /mnt/usr, I see files...

---

### Post by emmiesix on 2011-05-05
Ok, I tried doing the following:

mount /dev/sda1 /mnt
mount /dev/sda5 /mnt/usr
mount /dev/sda7 /mnt/boot
mount /dev/sda9 /mnt/root

then,

mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
mount --bind /usr/ /mnt/usr

plus two things from the kansasnoob post you pointed me to:


mount --bind /dev/pts /mnt/dev/pts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

The last one gave me an error and I had to delete the mnt/et/resolv.conf in order to do the copy, not sure why.

Anyway, I then tried to run various update commands in the order you suggested and I was getting tons and tons of errors.  It was connecting to the internet ok, but otherwise all kinds of broken dependencies... it seems like it must be missing something in the essential file structure.

I restarted the computer which was perhaps stupid, but I wanted to see if it helped the main install (it did not). So I'm back at trying this again.

---

### Post by emmiesix on 2011-05-05
A quick question:  Can anyone explain to me the purpose of the exact 

mount --bind

commands?  I am not clear on why those four directories, only, are being mounted in that way.

---

### Post by oldfred on 2011-05-05
Generally only servers or advanced users with very specific special requirements have separate system partitions. So yes if you also have other system partitions you need to mount them also. I do not know inner working of chroot.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by emmiesix on 2011-05-05
Ok, I think I figured out one source of the errors (something like it was reaching maximum reports) -- I needed to mount --bind /var to the local disk as well, as the usb key didn't have enough space for all the new package files.

Still updating...

---

### Post by oldfred on 2011-05-05
I only have in my notes, the additional mounting of /boot, but in your case I think you have to mount all system partitions separately.

mount /dev/sda5 /mnt
#if /boot
mount /dev/sda2 /mnt/boot

So likewise you need to do /boot, /usr, /opt. Not sure about /tmp as it is just used for temporary use, but if not there things may not work, so I would mount it also.

I do not understand if sda1 is / what is sda9. There is no /root as root really is /?

While maybe worth the effort to get it working & understand system. But it may be time to reinstall with just / (root), swap & /home. If lots of data in data partitions I leave /home inside / and link in data folders. Internal /home then really only has the mostly hidden user settings. I aggressively move any hidden data folders like Firefox & Thunderbird to /data also, so /home is only settings & small. Mine is 1GB and 3/4's is .wine which I have not moved to /data (yet).

---

### Post by emmiesix on 2011-05-05
well I managed to get enough things mounted to download the packages and now networking is up, and I have run recovery mode, fixing broken packages until there is nothing left to fix.

The problem is now that I can't get the GUI desktop to launch (I have tried reinstalling it and xorg).  I get weird driver errors when trying to, e.g., 

startx

from recovery mode command line.  I'm going to start a new thread because this is pretty far from where I've started.

THANK YOU for all the help, though.

---

### Post by perspectoff on 2011-05-05
sudo mkdir /media/partsda6
sudo mkdir /media/partsda7
sudo mount /dev/sda6 -t ext4 /media/partsda6
sudo mount /dev/sda7 -t ext4 /media/partsda7

Then merely copy the contents from one partition to the other:

sudo cp -a /media/partsda6/* /media/partsda7

---

