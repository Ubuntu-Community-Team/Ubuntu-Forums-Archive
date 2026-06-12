---
title: "A question of mounting hdd partitions the ubuntu way"
date: 2012-08-23
forum: General Help
---

### Post by beopen on 2012-08-23
hi,
i use ubuntu 10.04 LTS lucid.
In the course of learning with another linux i stumbled upon the issue of auto detecting and auto mounting internal partitions of hdd.
A search on the net reveals a common answer for the same which is 
1.create a permanent mount folder, 
2.create an  fstab entry
and therafter you can see your other partitions of hdd whether windows or non-ubuntu.
This is a common answer you can see on the net and the official answer too.
I am but quite perplexed how ubuntu does the same in a different way and nowhere i found how they do. 
1.In lucid i find all partitions are shown on the left side in the file manager.[ auto-detected]
2. when you click the one you want it gets mounted 'on the fly ' and you can see the triangle above a rectangle sign besides the partition name when it gets mounted.[auto-mounted]
3.You click that partition for unmounting, it gets unmounted on the fly.
4. In all these cases i found there is 
           a. no permanent mount folder created. Rather ubuntu lucid mounts partitions on-the-fly in the media folder. In which it creates a 'temporary folder' carrying the name of the label of the partition or the uuid as i find in my system. 
b. As soon as you unmount the same folder vanishes into thin air.
c.No fstab entry is there for the partitions which are thus mounted. My ubuntu fstab has only entries for the parititons created when installing ubuntu viz [root,boot,home,swap]. Yet it mount 2 ntfs partitions this way without an fstab entry. Partitions of a 2nd hdd are also loaded the same way without an entry for them in fstab.
d.Even If you create a new partition in the session, the same gets again seen right on the spot and if clicked gets mounted on the spot.
5 If all non-ubuntu partitions are unmounted the media folder has just two items a folder named floppy0 and a link named floppy. Thus there is no permanent folder for mounting.

Thus this system of ubuntu seems quite different to the most common answer found on the net as i mentioned above earlier to autodetect and automount other partitions.
My question is 
1.How ubuntu does this.
2. Can i replicate the same on another linux eg on my arch linux i can see only my arch linux partitions in the filemanager, if i want to see ubuntu partitions i need to go the fstab way. How can i get it done like ubuntu does it? Upon opening the filemanager you see all your other partitions on the left side of the explorer and if you click them they get mounted and unclick they get unmounted.
3.If yes Pls suggest how to do the same.

regards

---

### Post by LewisTM on 2012-08-23
Ubuntu uses GIO/GVFS and FUSE, a daemon and set of tools to let users mount partitions and network locations on-the-fly. This solves the problem that some users may not have sudo privileges to mount disks or access network filesystems. Disks get mounted in /media, network locations (FTP, SMB, etc) in ~/.gvfs
A good way to know what happened to the mounted partitions is to just run [FONT="Courier New"]mount[/FONT] in a terminal, it will display the contents of /etc/mtab including any user-mounted locations.

To automate the process you can take a look at gigolo, a friendly frontend to gvfs mount operations, and at the gvfs-mount and gvfs-open commands.

I agree the tutorials are very old-school Linux and don't talk about new, more "modern" ways of dealing with user locations. The new ways are more transparent but give you less control, maybe some users don't like that.

Cheers!

---

### Post by oldfred on 2012-08-23
I mount some partitions with fstab and label all my others that I rarely use, so I can easily tell what they are.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

You can manually mount each time you boot:
I learned a while back to stop using spaces. Use CamelCase or under_score or just onename. Windows will work without the spaces and it makes things a lot simpler in Linux.

sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
chmod -R a+rwX,o-w /mnt/data
sudo chown $USER:$USER /mnt/data
#if not known to list partitions
sudo fdisk -l

# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/data
** Then add the template with the correct UUID and mount point to fstab:
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

I normally suggest separate NTFS shared data partition and mounting the Windows system partition read-only.

Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862:](http://ubuntuforums.org/showthread.php?t=2043862:)
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.

---

### Post by techexpert666 on 2012-08-24
A link for fdisk tutorial:

[http://www.expertslogin.com/linux-administration/how-to-create-new-partition-filesystem-on-linux/](http://www.expertslogin.com/linux-administration/how-to-create-new-partition-filesystem-on-linux/)

---

