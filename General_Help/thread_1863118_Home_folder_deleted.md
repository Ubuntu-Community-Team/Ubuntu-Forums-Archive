---
title: "Home folder deleted"
date: 2011-10-17
forum: General Help
---

### Post by killvenom on 2011-10-17
Hi guys!
Although I have been using Ubuntu for one and a half years I consider my self a Linux n00bie.

I would like to get in straight to the issue.
I will give a somewhat in-depth description of my actions preceding the error as I am not completely sure what caused it. Maybe you can at least help me with finding that out. 
Two days ago I was finally able to set up broadband at my new flat. That was the reason why I hadn't updated Ubuntu for 40 days. There were about 85 packages that were updates. There were at least two kernel header updates in that list.
After doing that I was prompted to reboot the machine. Everything was fine after this first reboot. I spent several hours working on the machine and decided to fix a few problems with it. First of all I used the command $sudo pkill gnome-panel because some of the status icons were jumbled up. This fixed the issue. Then I went on to try and fix a second problem - making the internal speakers stop working when a headphone jack was plugged in. I installed a package that was recommended on some website. This package was from the supported repositories and wasn't a third party one. It had something to do with "ALSA".
When that was finished I decided to reboot my laptop for a second time. Upon logging in I was confused and thought that somehow I had logged into the Guest account. I quickly realised however that I was logged in with my user.
The system was as if I had done a fresh install. All my settings for the applications I tried to launch were gone. The desktop wallpapers were gone. All my most important files and information were on that system and in the home folder (I know... a terrible blunder on my part). I realised that the /home folder has been deleted and decided to turn off my laptop to prevent overwriting any files and maybe use some recovery software.
I have Win7 as my second operating system and decided to boot into it (hopping that because it has a different filesystem this would affect my linux partition). I did some research and in the mean while downloaded an image of Ubuntu and made a LiveUSB.
I switched that on and tried to find my files on the partition. The home folder was completely empty. I tried searching in ./Trash but there wasn't anything there as well. I found a [tutorial]("http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/") that mentioned scalpel, testdisk and a few other ways to recover my files. I tried them all but I wasn't really sure what I was doing. So that didn't help. I tried compiling extundelete but I wasn't able to.

So that's it.
My system is Ubuntu 10.04 LTS 64-bit. Dual booted with Windows 7 64-bit.
I have attached a .txt file with output from CPU-Z so you can see my hardware specs.

If you need any more info... I'm here.

My two main concerns are:
1. Would I be able to recover my files?
2. What could have cause this problem?

cheers

---

### Post by blueridgedog on 2011-10-17
> **killvenom said:**
> 
1. Would I be able to recover my files?
2. What could have cause this problem?


Welcome to the forums.

One potential reason could have been having your /home folder on a separate partition that is somehow not being mounted.  We can take a look at your partitions if you post the output of:

```
mount
```

and

```
sudo fdisk -l
```

(A lower case "L")

I have had little luck restoring files that were deleted, but perhaps others can give tips on that.

---

### Post by killvenom on 2011-10-17
Sorry for replying prematurely.
I just wanted to add that I have 2 NTFS partitions (Windows and Data) and an ext4 partiotion for my Ubuntu. Hope that clears things up a bit. I'll try and give you the output for these tomorrow.

cheers!

---

### Post by killvenom on 2011-10-20
Dunno if this is allowed but could I ~Bump this thread.
I basically lost everything because of this error.
All I want to know is what it cause it.

---

### Post by cryptotheslow on 2011-10-20
Please provide the information blueridgedog requested.

One potential reason could have been having your /home folder on a  separate partition that is somehow not being mounted.  We can take a  look at your partitions if you post the output of:

 ```
    mount   
```

and

```
  sudo fdisk -l 
```

(A lower case "L")

---

### Post by killvenom on 2011-10-24
Sorry for not replying sooner. Hope you can figure out something.
Here you go:

Output form MOUNT:

```
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
```


Output for FDISK -L

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001e3ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        4093    32765952    7  HPFS/NTFS
/dev/sda3            4093       47360   347548599+   7  HPFS/NTFS
/dev/sda4           47360       60802   107968513    5  Extended
/dev/sda5           47360       60250   103534592   83  Linux
/dev/sda6           60250       60802     4432896   82  Linux swap / Solaris

Disk /dev/sdb: 4043 MB, [4043308544]("tel:4043308544") bytes
4 heads, 32 sectors/track, 61695 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00089913

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18464     1181695+   7  HPFS/NTFS

```

---

### Post by cryptotheslow on 2011-10-24
Can you also please post the output of:

```
cat /etc/fstab
```That is the text file containing the definitions of filesystems.

If you browse to /home is there a directory in there with your username as its name?

If there is, are there any files in there that you recognise?

Also do you happen to see files called .Private, .Ecryptfs and a directory named Private?

N.B. The files above starting with a dot . will normally be hidden - Ctrl + H will usually unhide them - or find the option to "Show Hidden Files" in the menu.

---

### Post by blueridgedog on 2011-10-25
Are you booted off of a CDROM or USB drive?  I ask because your mounts are:

```
aufs on / type aufs (rw)
/dev/sdb1 on /cdrom type vfat
```

As far as disks, it appears you have:

```
Disk /dev/sda: 500.1 GB
```

With five partitions:

```
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
/dev/sda2              13        4093    32765952    7  HPFS/NTFS
/dev/sda3            4093       47360   347548599+   7  HPFS/NTFS
/dev/sda5           47360       60250   103534592   83  Linux
/dev/sda6           60250       60802     4432896   82  Linux swap / Solari
```s

And a 4 gig (USB?):

```
Disk /dev/sdb: 4043 MB
```

With only one partition:

```
/dev/sdb1   *           1       18464     1181695+   7  HPFS/NTFS

```

So, your linux installation is sda5, your windows recovery partition is likely to be sda1, windows install likely to be sda2 and a data partition of sda3.

I can talk you through mounting these and seeing what is on them, but I want to understand how your are booted first.

As and asice, you can see what is on your linux partion with:

```
sudo mkdir /mnt/linuxinstall
sudo mount /dev/sda5 /mnt/linuxinstall
cd /mnt/sda5/home
ls -al
```

From there you can also cd into your user directory and see if your files are there.

---

### Post by killvenom on 2011-10-25
@cryptotheslow

Here is the output:
```

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```
To answer your other questions:
Yes I have a folder with my username. All the folders in here are empty. I am not certain but I think that  most of the (dot) folders have been created when I logged back in and  found that my files had gone.
As you can see there are no .Private files.

```

ubuntu@ubuntu:/media/HDD/home/USERNAME$ ls -al
total 312
drwxr-xr-x 29 1000 1000   4096 2011-10-15 14:42 .
drwxr-xr-x  3 root root   4096 2010-09-10 17:44 ..
drwx------  4 1000 1000   4096 2011-10-15 14:35 .adobe
-rw-------  1 1000 1000    231 2011-10-15 14:30 .bash_history
drwxr-xr-x  2 1000 1000   4096 2011-10-15 14:34 .blueproximity
drwxr-xr-x  4 1000 1000   4096 2011-10-15 14:37 .cache
drwx------  3 1000 1000   4096 2011-10-15 14:30 .compiz
drwxr-xr-x  8 1000 1000   4096 2011-10-15 14:39 .config
drwx------  3 1000 1000   4096 2011-10-15 14:34 .dbus
drwxr-xr-x  2 1000 1000   4096 2011-10-15 14:34 Desktop
-rw-r--r--  1 1000 1000     41 2011-10-15 14:37 .dmrc
drwxr-xr-x  2 1000 1000   4096 2011-10-15 14:34 Documents
drwxr-xr-x  2 1000 1000   4096 2011-10-15 14:34 Downloads
-rw-------  1 1000 1000     16 2011-10-15 14:20 .esd_auth
drwxr-xr-x  2 1000 1000   4096 2011-10-15 14:35 .fontconfig
drwx------  5 1000 1000   4096 2011-10-15 14:37 .gconf
drwx------  2 1000 1000   4096 2011-10-15 14:42 .gconfd
-rw-r-----  1 1000 1000      0 2011-10-15 14:36 .gksu.lock
drwx------  6 1000 1000   4096 2011-10-15 14:42 .gnome2
drwx------  2 1000 1000   4096 2011-10-15 14:34 .gnome2_private
-rw-r--r--  1 1000 1000    142 2011-10-15 14:37 .gtk-bookmarks
drwx------  2 1000 1000   4096 2010-09-10 17:49 .gvfs
-rw-------  1 1000 1000   1026 2011-10-15 14:37 .ICEauthority
drwxr-xr-x  3 1000 1000   4096 2011-10-15 14:34 .local
drwx------  3 1000 1000   4096 2011-10-15 14:29 .macromedia
drwx------  4 1000 1000   4096 2011-10-15 14:38 .mozilla
drwxr-xr-x  2 1000 1000   4096 2011-10-15 14:34 Music
drwxr-xr-x  2 1000 1000   4096 2011-10-15 14:34 .nautilus
drwxr-xr-x  2 1000 1000   4096 2011-10-15 14:34 Pictures
drwxr-xr-x  2 1000 1000   4096 2011-10-15 14:34 Public
drwx------  2 1000 1000   4096 2011-10-15 14:37 .pulse
-rw-------  1 1000 1000    256 2011-10-15 14:20 .pulse-cookie
-rw-------  1 1000 1000 159252 2011-10-15 14:42 .recently-used.xbel
drwxr-xr-x  3 1000 1000   4096 2011-10-15 14:30 .Skype
-rw-r--r--  1 1000 1000      0 2011-10-15 14:28 .sudo_as_admin_successful
drwxr-xr-x  2 1000 1000   4096 2011-10-15 14:34 Templates
drwx------  2 1000 1000   4096 2011-10-15 14:36 .update-notifier
drwxr-xr-x  2 1000 1000   4096 2011-10-15 14:34 Videos
-rw-------  1 1000 1000   4684 2011-10-15 14:42 .xsession-errors
-rw-------  1 1000 1000   4584 2011-10-15 14:36 .xsession-errors.old

```

@blueridgedog

I think the output would answer your question as well.

---

### Post by killvenom on 2011-10-30
Well? 
Any ideas :(

---

### Post by killvenom on 2011-12-29
I think it's about time I got rid of my Ubuntu partition since it's taking up 160GB of my harddrive.
I was considering using Partimage to back it up but it seems like to much of an effort.
One last question I want to ask is:
  If I was to delete and format the partition, would GRUB2 still 
  work fine?

cheers

---

