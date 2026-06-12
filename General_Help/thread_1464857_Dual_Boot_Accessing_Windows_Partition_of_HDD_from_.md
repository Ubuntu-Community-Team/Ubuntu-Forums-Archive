---
title: "Dual Boot: Accessing Windows Partition of HDD from Lucid"
date: 2010-04-28
forum: General Help
---

### Post by jonny163 on 2010-04-28
Hey guys, a question that I don't know is n00bish or not :S
I have dual booted Windows 7 and Lucid 10.04 but most of my files are in the partition of the HDD belonging to 7.
Is there a way, besides copying the files across to the Lucid partition, to be able to access the files for the likes of backgrounds, screensavers, sound apps etc? (I am thinking that the music app will have to have the file pathway before playing it like in iTunes on 7)
The reason I am asking is because I have a small hard disk drive on my netbook and do not want to have to copy all the files across

---

### Post by Leppie on 2010-04-28
install ntfs-config which is a simple tool that takes away the pain of setting up your system to mount the ntfs partition:
```
sudo apt-get install ntfs-config
```
once you have access to the ntfs partition, you can create symlinks to the files/folders on the windows partition. just bear in mind that if there's spaces in the file/folder names, you need to place a backslash in front of it:
```
ln -s /path/to/windows/Users/Default\ User/funkyfile
```
or use quotes:
```
ln -s "/path/to/windows/Users/Default User/funkyfile"
```

---

### Post by jonny163 on 2010-04-28
Thank you, that worked perfectly :D

EDIT: It actually didn't work perfectly :S
It created a link but the link doesn't work, I think I used the wrong pathway.
The 7 partition is already accessible while on Lucid but it reads as a mountable drive, it's path is /media/4A30C94A30C93E27
or possibly /media/77\ GB\ Filesystem/

---

### Post by Leppie on 2010-04-28
in ntfs-config did you not label the partition?
names like "4A30C94A30C93E27" are not very descriptive nor useful, in ntfs-config change it to something like "windows".

---

### Post by jonny163 on 2010-04-29
Yeah, ntfs config...
I did a botch job with my friend and didn't actually configure it because my HDD was already split halfway into a C: and D:
I can go do it now, though, right? Rename the partition?

---

### Post by Detonate on 2010-04-29
You can simply add a line to your /etc/fstab file that will automatically mount the windows partition at boot.

This is the entry from my fstab that does this with full read write permissions for the user.

[COLOR="Blue"]/dev/sda2 /mnt/Windows ntfs-3g uid=1000,gid=1000,locale=en_US.UTF-8 0 0[/COLOR]

Of course you need to create the mount point first with the command
```
sudo mkdir /mnt/Windows
```

Edit the fstab entry to change the partition to be mounted to whichever partition your Windows is on.

---

### Post by Leppie on 2010-04-29
> **jonny163 said:**
> Yeah, ntfs config...
I did a botch job with my friend and didn't actually configure it because my HDD was already split halfway into a C: and D:
I can go do it now, though, right? Rename the partition?
yes, just launch ntfs-config and select the mount point(s) of your choice. it will take care of creating an entry/entries in your fstab (if necessary).

---

### Post by Mark Phelps on 2010-04-29
While individual experiences always vary, I've personally found it to be a bad idea to automount MS Windows OS partitions read-write.

If the machine shuts down suddenly, that leaves the MS Windows OS in a bad state.  You won't then be able to mount it in Ubuntu.  If you can boot into MS Windows and run chkidsk, you're then generally OK.

But if the partition was an OS partition, and it now won't boot -- you're hosed.

I've personally found it a better practice to share DATA partitions (NTFS formatted).  That way, you can always boot into an OS partition and run chkdsk.

---

### Post by Detonate on 2010-04-29
> **Mark Phelps said:**
> While individual experiences always vary, I've personally found it to be a bad idea to automount MS Windows OS partitions read-write.


As you said, individual experiences may vary.  I've been automounting my Windows partition ever since linux first got ntfs support years ago, and I've never had a problem.  I feel the convenience of being able to access my ntfs partition far outweighs the slight risk of file corruption that might occur.

Your idea of a separate partition, to mount ntfs files is good, but in the case of the original poster, disk space is at a premium on his machine.

---

### Post by jonny163 on 2010-04-29
> **Leppie said:**
> yes, just launch ntfs-config and select the mount point(s) of your choice. it will take care of creating an entry/entries in your fstab (if necessary).

Ok, I made the mount point /media/7
What do I do now? I don't really understand terminal as I am totally new to Linux.

---

### Post by Leppie on 2010-04-29
once you've done that, it should appear under /media/7/
try accessing it before creating symlinks to files on that partition. also keep in mind that if using symlinks to this partition, you may want to set it to automatically mount at system start (can also be configured with ntfs-config) as otherwise the symlinks will not work until the partition is mounted.

---

### Post by jonny163 on 2010-04-29
I don't understand the code for creating these symlinks

```
ln -s /path/to/...(what goes here?)
```

I don't think my ntsf-config does that, here is a screenie

[IMG]http://img135.imageshack.us/img135/3000/screenshotbc.png[/IMG]

Also, the drive is now on the desktop. I would prefer a clean desktop to being able to access the 7 partition. (Sorry for being awkward :S)

---

### Post by Leppie on 2010-04-29
replace the "/path/to/windows/" part with "/media/7/":
```
ln -s /media/7/Users/<username>/funkyfile
```

---

### Post by jonny163 on 2010-04-29
Thanks so much, that seems to have worked minus the funkyfile part.
How can I automount it with ntfs-config?

---

### Post by Leppie on 2010-04-29
sorry for not explaining that.
to be honest i haven't used it in a while and couldn't find the settings after installing ntfs-config so i just rebooted and the partition was mounted when i logged on.
so you're all set ;)

---

### Post by jonny163 on 2010-04-29
No need to apologise, you are helping me :D
Ok thanks I will test it. Does it mean that it will always be present on the desktop?

---

### Post by Leppie on 2010-04-29
> **jonny163 said:**
> No need to apologise, you are helping me :D
Ok thanks I will test it. Does it mean that it will always be present on the desktop?
yes, it will always be present on the desktop.
if you prefer not to have it on the desktop, copy the concerning entry from your fstab and remove the ntfs-config application from the system after which you should copy back the entry in your fstab file. or go into the gnome configuration editor and remove it there.

---

### Post by Morbius1 on 2010-04-29
(1) The dialog box pictured in post 12 is why I will never use ntfs-config. Is it not aware that ntfs is writeable by default and doesn't need to have "write support enabled".

(2) Partitions mounted in /media or in /home/user_name will create an icon on th desktop. Partitions mounted on /mnt or / will not.

(3) FYI, if you were to allow Ubuntu to set up these non-system partitions at install time it would look something like this depending on where you tell it you want it mounted:

```
UUID=DA9056C19056A3B3 /windows/D      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```This will mount an ntfs partition to /windows/D ( in this case ) with read write access to owner and group and no one else ( the umask=007 part ). The gid=46 is group=plugdev. All members of plugdev will have read/write access and all local login users are members of plugdev by default.
[COLOR=Blue]
EDIT:[/COLOR] Not that you care but I agree with Mark Phelps above concerning write access to the Windows system disk ( i.e., C - Drive ). After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.

---

### Post by jonny163 on 2010-04-30
Morbius1, thanks for being concerned about all my files :D (at least that's what I think you meant). I intend to back everything up regularly just in case.

My excursion into fstab didn't work (my friend didn't know about fuseblk which appeared in it), however, he came across a command to prevent any drives from appearing on the desktop which is ideal.

```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

Obviously, if you want to see them again you set it to 'true'

Thank you so much for all your help :D

---

### Post by nanog on 2010-04-30
> But if the partition was an OS partition, and it now won't boot --  you're hosed.

You are not hosed. Testdisk can repair partition/mbr problems. The much easier to use (but closed source shareware) bootit-ng will also fix just about any partition/mbr problem.

---

### Post by Morbius1 on 2010-04-30
> **jonny163 said:**
> Morbius1, thanks for being concerned about all my files :D (at least that's what I think you meant). I intend to back everything up regularly just in case.

My excursion into fstab didn't work (my friend didn't know about fuseblk which appeared in it), however, he came across a command to prevent any drives from appearing on the desktop which is ideal.

```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```Obviously, if you want to see them again you set it to 'true'

Thank you so much for all your help :D

The only problem with your friends solution is that the next time you insert a USB drive it's icon also will not be on the desktop. I'm the type of person who needs reminders on the desktop that a usb drive is still mounted and needs to be safely unmounted before I can remove it. Perhaps you have a better attention span than I do :wink:

---

### Post by jonny163 on 2010-04-30
Yeah, I prefer to keep my desktop clean. I can take that little extra time to go to Places and unmount that way, or terminal umount. But the chances that I use a USB, or the like, in Ubuntu are rare because I mostly use them for copying university work, which I do in Windows.

---

