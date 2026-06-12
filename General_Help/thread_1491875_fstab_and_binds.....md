---
title: "fstab and binds...."
date: 2010-05-24
forum: General Help
---

### Post by stewils on 2010-05-24
Not quite sure what, but small change after a couple of days of unsucsess and a reboot seem to have sorted the problem...seconds after I post for help...

> I have a duel boot machine, ubuntu and Win7.
I'm trying to bind windows documents folder to ubuntu docs,
My external hard drives pictures folder to Ubuntu Pics, 
and the same with the music and video folders on the external drive.

when I do 

**sudo mount --bind /media/"Pics and Music"/Music /home/ste/Music**

all works well, but the line 

**/media/Pics\040and\040Music/Music           /home/ste/Music     none  rw,bind                  0  0** 

in **/etc/fstab** doesn't seem to do anything and 

**sudo mount all** tells me mount: can't find all in /etc/fstab or /etc/mtab

Here's my fstab in full.
[QUOTE]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc               proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda5 during installation
UUID=9353f920-b9e0-465b-824f-785210f0a668   /                   ext4  errors=remount-ro        0  1  
# swap was on /dev/sda6 during installation
UUID=49c72ffc-35e2-4b62-8663-3f414b049556   none                swap  sw                       0  0  
/dev/sdb1                                   /media/Pics\040and\040Music         ntfs  nls=iso8859-1,umask=000  0  0  
/dev/sda2                                   /media/Windows      ntfs  nls=iso8859-1,umask=000  0  0  
/media/Pics\040and\040Music/My\040Pictures  /home/ste/Pictures  none  rw,bind                  0  0  
/media/Pics\040and\040Music/Music           /home/ste/Music     none  rw,bind                  0  0  
/media/Pics\040and\040Music/Vids            /home/ste/Videos    none  rw,bind                  0  0  
[/QUOTE]

---

