---
title: "Can't access ANY of my HDDs"
date: 2009-12-07
forum: General Help
---

### Post by djm227 on 2009-12-07
Earlier today I was running a triple boot with 7, xp, and ubuntu...and everything was working fine.  All of my backups from XP were complete, so I booted into windows 7 and got rid of my XP install (through formatting).  So now I have Windows 7 and Ubuntu.  But I having a few major problems.

1: Hard drives other than current will NOT open, unless I physically mount each one after each start up.  I get this error when I try to open one:
> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.2:  Grub won't update.  3 different "ubuntus" show up on boot now under grub, and my XP installation is still there.  I tried updating grub, but I only get this:
> xxx@xxx-desktop:~$ sudo grub-update
[sudo] password for xxx: 
sudo: grub-update: command not found
xxx@xxx-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/My: No such file or directory
3. I can NOT restart or shutdown Ubuntu.  If I try, it hangs on the screen:
> 
Ubuntu 9.10 xxx-desktop tty1
xxx-desktop login:


---

### Post by Toast2120 on 2009-12-07
Can you list the HDs on which each OS was installed. For example, were Windows and Ubuntu on seperate HDs as XP?

---

### Post by djm227 on 2009-12-07
> **Toast2120 said:**
> Can you list the HDs on which each OS was installed. For example, were Windows and Ubuntu on seperate HDs as XP?

XP was on it's own HD, one partion.  Windows 7 and Ubuntu were on the same HD, with some free space left over.

I also have one 300 GB internal and a 500 external for storage.  I can sometimes open the 500, but all of the other ones are a no-go.

---

### Post by djm227 on 2009-12-07
Error message received while attempting to access one of the HDDs:

>  DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by fluffman86 on 2009-12-07
try this in Applications > Accessories > Terminal:
```
sudo fdisk -l
```
to see where each partition is.  Then do:
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1 -t ntfs-3g -o force
```
To attempt to force your drives to mount.  This will only work for your NTFS drives, and you should replace the "sda1" parts with the information you from the fdisk command that list the "System" as "HPFS/NTFS".

---

### Post by djm227 on 2009-12-08
Thanks for those commands.  That does work in allowing me to access my files...but I still have to do it every time I reboot.  I added some more info in my original post explaining my problem a little bit more.

If anyone knows what to do I would really appreciate it.  I'm trying to avoid a reinstall here....in fact I'm not even sure that would help since the problem seems to be with grub.

---

### Post by Jive Turkey on 2009-12-08
now that we know your other HDD can be mounted we need to add it to your /etc/fstab file to make it mount automatically at boot time.

google "fstab mount ntfs" and you will find lots of guides for this.

You will need the UUID of the drive to do this, you will also be able to set the read/write permissions for it in fstab.  You will also need to designate a mountpoint for the drive (an empty folder).

Someone correct me if I'm wrong but I believe you will not be able execute files that are on an ntfs partition under linux, so down the road remember if you are having problems with that.

Once you have made the entry in fstab for the drive, the command ```
sudo mount -a
``` will mount it (and any other drive in fstab.  this will be helpful to test your config without rebooting every time you tweak it.

---

### Post by oldfred on 2009-12-08
When you install a second windows like win7 it moves its boot files into the current windows that has the boot flag on. If you for instance then delete the XP install partition you have no boot flag and are missing some of the win7 boot files. You need to use gparted to set boot flag on the win7 partition and use the win7 CD/DVD to repair the win7 install. It will probalby overwrite your grub so be prepared to reinstall that also after you have booted win7 several times to make sure it is ok. Then the update-grub will find the working win7 install.

---

### Post by djm227 on 2009-12-08
> **oldfred said:**
> When you install a second windows like win7 it moves its boot files into the current windows that has the boot flag on. If you for instance then delete the XP install partition you have no boot flag and are missing some of the win7 boot files. You need to use gparted to set boot flag on the win7 partition and use the win7 CD/DVD to repair the win7 install. It will probalby overwrite your grub so be prepared to reinstall that also after you have booted win7 several times to make sure it is ok. Then the update-grub will find the working win7 install.

Thanks for the reply.  What if the boot flag is already checked when I look at that partition in gparted?  My windows boots and operates fine, for some reason my Ubuntu is the one affected.  Does gparted manage the mounting of my hard drives, which is why it's all messed up in Ubuntu?

Thanks again, I'm a noob so I'm trying the best I can to understand this.

---

### Post by oldfred on 2009-12-08
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

---

