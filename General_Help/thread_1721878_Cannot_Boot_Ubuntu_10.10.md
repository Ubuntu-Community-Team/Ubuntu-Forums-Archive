---
title: "Cannot Boot Ubuntu 10.10"
date: 2011-04-05
forum: General Help
---

### Post by JohnBUK on 2011-04-05
I've been an idiot and think I've deleted a whole lib folder! The screen went black and now will not boot up.
I was trying to uninstall a PPA for mounting my iTouch (ppa:pmcenery/ppa) (it didn't work) and found what I guess was the folders where the dependencies were installed. Pressed delete by accident on a folder which I think was entitled "lib etc" or similar and the world dropped out. In my panic I forgot how I got to that screen or what the folder/files were called. 
As I run two websites from this laptop using Net Objects Fusion on Vista in Virtualbox I don't really want to reinstall the whole OS - I also have a lot of photos on my Vista OS which I sometimes boot into (dual boot). 

If I boot from a Live CD would I be able to find the missing folder/files and then copy them to the OS?

Or if there are any alternatives you can suggest I'd be very grateful.

Thank you.
JB

---

### Post by nothingspecial on 2011-04-05
If you've deleted /lib your installation is toast.

Boot from a live cd, copy your data across and reinstall.

---

### Post by JohnBUK on 2011-04-05
OK as I feared. I'm looking now to see if I can id which folder is missing.

---

### Post by JohnBUK on 2011-04-05
OK, the Lib folder IS there, can anyone suggest a way of determining which files/folders are missing from this installation? Is there a way of comparing with the working Live CD perhaps - I do accept that over time my original install will have many other files but if we assume the issue is one of an OS file/folder ftb.
Thanks
JB

---

### Post by nothingspecial on 2011-04-05
You could try chrooting from a live cd

Boot it up, click your harddrive in the places menu to mount it

then type ```
mount
``` or ```
fdisk -l
``` to find out what /dev/sd?? it has been assigned.

Then ```
chroot /dev/sd??
```

Then try ```
apt-get install -f
```

I doubt that will work though.

---

### Post by JohnBUK on 2011-04-05
Thanks for your prompt replies, would you just explain what the terminal instructions in last message will do (in newbie terms please).
Thanks
JB

---

### Post by nothingspecial on 2011-04-05
The first 2 will find out what your internal hard drive is known to the livecd as. It will be something like /dev/sdb1

chroot will allow you to use the live cds working apps on the borked system

apt-get install -f will try to fix any broken packages by installing unmet dependencies such as the libs you have deleted

You could also try looking in /home/$USER/.local/share/trash to see if you just moved the folder to trash (change $USER to your actual username, john I'm guessing:P)

---

### Post by JohnBUK on 2011-04-05
To "nothingspecial"

Thanks for sticking with me!! Sadly the files don't appear in the /home/john/.local/share/trash folder - it has a large white cross on the icon as well for some reason? 

I'll run the terminal shortly as a last resort I guess!
I'm grateful for your help thus far.

John

---

### Post by nothingspecial on 2011-04-05
They might be in root's trash.

Did you click delete or use rm

---

### Post by JohnBUK on 2011-04-05
OK "mount" brings up the following:
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
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
/dev/sr0 on /media/apt type iso9660 (ro)
/dev/sda5 on /media/c735ac5c-38ba-4a1c-af11-0bf26f193ac4 type ext4 (rw,nosuid,nodev,uhelper=udisks)

I currently dual-boot into Ubuntu and Windows Vista (the original OS). Ubuntu has 70Gb partitioned and Windows some 80Gb with a recovery partition (Dell Laptop). 
"/dev/sda5" would seem the right partition as the long number following it "c735 etc" shows at the top of the screen when I click on that OS in Places.
Is that logical as far as you are concerned?
Obviously I guess I'll have to format the drive eventually but if I can get away with it I'd like to.
John

---

### Post by nothingspecial on 2011-04-05
That's the one, but have a look in /media/c735ac5c-38ba-4a1c-af11-0bf26f193ac4/root/.local/share/trash first

---

### Post by JohnBUK on 2011-04-05
root is also empty with a large white cross on.

---

### Post by JohnBUK on 2011-04-05
Sorry, in answer to the second part of your post, I'm pretty sure I right-clicked and pressed "delete".

---

### Post by beew on 2011-04-05
Just wondering how it is possible to delete a system folder by accident. You need to be root to delete it.

---

### Post by nothingspecial on 2011-04-05
Then the files should be there.

---

### Post by JohnBUK on 2011-04-05
> **nothingspecial said:**
> That's the one, but have a look in /media/c735ac5c-38ba-4a1c-af11-0bf26f193ac4/root/.local/share/trash first
No, empty, and white cross.

---

### Post by nothingspecial on 2011-04-05
Ok, do this

```
sudo mount &#8208;&#8208;bind /dev /media/c735ac5c-38ba-4a1c-af11-0bf26f193ac4/dev
sudo mount &#8208;&#8208;bind /proc /media/c735ac5c-38ba-4a1c-af11-0bf26f193ac4/proc
sudo mount &#8208;&#8208;bind /sys /media/c735ac5c-38ba-4a1c-af11-0bf26f193ac4/sys
sudo chroot /media/c735ac5c-38ba-4a1c-af11-0bf26f193ac4
sudo apt-get install -f
```

---

### Post by JohnBUK on 2011-04-05
> **beew said:**
> Just wondering how it is possible to delete a system folder by accident. You need to be root to delete it.
To be frank it was late last night, and I was "cleaning" my laptop per Ubuntu Tweak, Synaptic etc and somehow I came across a box with the PPA I mentioned above and recognised it as having been that I'd tried to uninstall earlier that evening. There were, I think, 5 orange folders showing (although I thought they were files at the time) with "ticks" next to them. So as I thought they'd already been deleted I right-clicked the top folder with the PPA name and deleted it - no problem. Chose the second folder and did likewise but nothing happened, so I chose the last folder and did similarly and that's when everything collapsed.
I know it's silly and entirely my stupidity. I've run Ubuntu for over a year now, dabble with the terminal (parrot-fashion) dual-boot and run a virtual machine but it goes to show that a little knowledge is a dangerous thing. Got complacent and Bam!
The trouble is I cannot replicate where I was in the system to give any better clues as to what may have happened.
John

---

### Post by JohnBUK on 2011-04-05
Ok copied and pasted the first line and this appeared. Tried to copy and paste second line but it won't accept!
ac4/dev
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo mount &#8208;&#8208;bind /proc /media/c735ac5c-38ba-4a1c-af11-0bf26f193ac4/proc
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo mount &#8208;&#8208;bind /proc /media/c735ac5c-38ba-4a1c-af11-0bf26f193ac4/proc
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo mount &#8208;&#8208;bind /proc /media/c735ac5c-38ba-4a1c-af11-0bf26f193ac4/proc
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo mount &#8208;&#8208;bind /proc /media/c735ac5c-38ba-4a1c-af11-0bf26f193ac4/proc
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

I'm sorry but this soesn't mean a lot to me.
John

---

### Post by nothingspecial on 2011-04-05
It means I've typed something wrong, hang on

---

### Post by JohnBUK on 2011-04-05
> **nothingspecial said:**
> It means I've typed something wrong, hang on
I'm really grateful for your help, but don't want to intrude on your life as it were! If you are busy etc then please feel free to bail out at any time. I feel embarrassed at causing you so much trouble for my silly error.

---

### Post by nothingspecial on 2011-04-05
> **JohnBUK said:**
> I'm really grateful for your help, but don't want to intrude on your life as it were! If you are busy etc then please feel free to bail out at any time. I feel embarrassed at causing you so much trouble for my silly error.

I'm avoiding doing the cleaning, which I'd better do. I can't see what I've done wrong with the chroot unless it has changed somehow since last time I did it.

To be honest, like I said in my 2nd (I think) post, I doubt it will work anyway.

---

### Post by JohnBUK on 2011-04-05
> **nothingspecial said:**
> I'm avoiding doing the cleaning, which I'd better do. I can't see what I've done wrong with the chroot unless it has changed somehow since last time I did it.

To be honest, like I said in my 2nd (I think) post, I doubt it will work anyway.
OK, I'm really grateful for your help, I'll go and bite the bullet and format the drive and reinstall. I'll take the opportunity to ditch the Windows Vista partition and run it on a VM for the website Net Objects Fusion program and the occasional iTunes.
John

---

