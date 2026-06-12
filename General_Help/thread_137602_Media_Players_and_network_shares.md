---
title: "Media Players and network shares"
date: 2006-02-28
forum: General Help
---

### Post by MarkLori on 2006-02-28
I just installed Ubuntu Breezy at home, ran Automatix (which is awesome!), to load most of the stuff I really will use, and set up a network to another machine that has all of my mp3's and video's, etc.  I got the printer sharing, internet sharing, and file shares set up and working fine.  
    The problem is that some programs (i.e. mplayer, xmmx, beep media player) don't want to see the share.  I can't find it under /media or /mnt.  Totem accesses the files if I drop them into it, but that does not work on the packages above. 
     Where do I find them in the file system?  They are on a standard Windows share. (Still maintained until I get better at gaming on Linux and find a verwion of Linux that will install and work on that box, one of the infamous HP pavilion a1130n's).

Thanks!

Mark

---

### Post by lapsey on 2006-02-28
[QUOTE=MarkLori]I just installed Ubuntu Breezy at home, ran Automatix (which is awesome!), to load most of the stuff I really will use, and set up a network to another machine that has all of my mp3's and video's, etc.  I got the printer sharing, internet sharing, and file shares set up and working fine.  
    The problem is that some programs (i.e. mplayer, xmmx, beep media player) don't want to see the share.  I can't find it under /media or /mnt.  Totem accesses the files if I drop them into it, but that does not work on the packages above. 
     Where do I find them in the file system?  They are on a standard Windows share. (Still maintained until I get better at gaming on Linux and find a verwion of Linux that will install and work on that box, one of the infamous HP pavilion a1130n's).

Thanks!

Mark[/QUOTE]

I have never used Automatix but I assume it is a networking setup wizard.

Gnome can handle samba shares but only via the smb:// protocol, as does Totem.

Others sucuser backups h as mplayer xmms etc cannot. My solution (rather than mount it via fstab, because Id rather mount when I want to) is to 

> 
sudo apt-get install smbfs

sudo chmod +s /usr/bin/smbmnt


(this makes it user-executable)

then I put the following in a launcher in a folder I want to mount:

> 
smbmount //server/share /home/myusername/folderiwanttomountto -o username=USERNAME,password=PASSWORD,fmask=755,dmask=755,rw

This way you just go into the folder, run the launcher and watch as the launcher is hidden by your samba shares. The launcher will return once the share is unmounted (on reboot or logout, i forget which)

you can fiddle about with the fmask and dmask if you dont want full priviledges :3


It's easy, you don't have to mess around with fstab and you can get it to run on gnome login or whenever you like just like any other command.

---

### Post by MarkLori on 2006-02-28
Thanks. Looks like it's what I need.  I'll try it out tonight.

---

