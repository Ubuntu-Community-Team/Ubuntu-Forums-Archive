---
title: "Syncing with a network folder"
date: 2011-02-07
forum: General Help
---

### Post by green_earth on 2011-02-07
I'm trying to sync to a folder on my NAS by synology. I have a large music folder that I use accross my network with Windows 7 computers, and my laptop now has 10.10. As I'd like to take the music with me on the laptop, I wish to sync from this network folder to the music folder in my home folder in Maverick. I wish to syncronize both directions. However, all the sync programs I've found and installed (unison, luckybackup, grsync) simply won't recognize the samba network mounted folder. I've tried bookmarking the location in Natilus, and pasting in the actual "smb" address to the drive location field to no avail. I'm a perpetual newbie more or less, so I don't know what to do next. The sync programs all want to work with a "local" folder/drive. Is there a way to trick them into thinking the folder is local? On Windows, I've not had any issue with sync programs such as goodsync or synctoy by mapping a network drive. I don't see a similar solution to this in Ubuntu. Any ideas?

---

### Post by rubylaser on 2011-02-07
Sure, unison will handle this for you.  I'd probably add a mount option in /etc/fstab to take care of mounting the Windows share.  Then, you'll easily be able to run Unison to sync both ways.
Make the mount point
```
sudo mkdir /var/music
```
Allow your user read/write
```
sudo chown <user>:<user> /var/music
```
*Replace <user> with your username
Edit /etc/fstab
```
sudo gedit /etc/fstab
```
Paste this at the bottom
```
//192.168.1.1/music    /var/music cifs  0    0
```
mount the share
```
sudo mount -a
```

Sync the files
```
unison /var/music /home/<user>/Music/
```
This would sync from your Windows share to your local user music folder.

That might not be clear enough to follow, so let me know if you need clarification.

---

### Post by green_earth on 2011-02-07
Rubylaser, thank you! So far so good... I'm halting at the edit of fstab to ask one quick question - is the //192.168.1.1/music a generic address to my windows share of the music folder I want to sync to, or do I need to find that exact address? Forgive the ignorance here, but I know that the address you specified is the address of my Linksys router, but I think the ip address of the Synology NAS is something different, and as the music folder is nested inside another folder, it might be something a little more unique? I can find the Synology ip address in windows, a little unclear as to how to find it in Ubuntu (but am sure its easy with the right terminal commands). Am I on the right track? Thanks again!

---

### Post by rubylaser on 2011-02-08
The 192.168.1.1/music is a generic ip address and share name.  The /music part will be whatever you made your share name. Your NAS ip address will be the same whether you get it from the Ubuntu install or your Windows machine, since you know how to get it from Windows, just get the ip from there.  Also, if you know what the path is to the share from Windows, if you paste it here, I'll show you the correct /etc/fstab line.

---

### Post by green_earth on 2011-02-09
Yup, got it figured out. I ended up using the authentication method as follows to connect to my share on my Synology NAS:

> 
//192.168.1.103/myshare/music /var/music cifs credentials=/home/greenearth/Documents/.psswrd,iocharset=utf8,codepage=cp850,noperm,auto 0 0

Otherwise, I followed your instructions exactly and I'm sync'ed up! Working perfectly! Thanks again for your help...

---

