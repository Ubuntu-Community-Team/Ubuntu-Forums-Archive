---
title: "Ubuntu won't Listen!  Permissions!"
date: 2011-01-28
forum: General Help
---

### Post by hogfan on 2011-01-28
I have a share that was working fine until I regorganized my folders.  I have a RAID 5 array mounted as /mnt/raid.  It is formatted as EXT4.   On the array are several folders:

Music
Movies
Concerts

Music used to contain two folders, MP3 Music & AAC (M4A) Music.  I consolidated all music in my MP3 Music folder into the AAC (M4A) Music folder, then removed the empty MP3 Music folder.  Then I tried to move all music in  AAC (M4A) Music up one level into simply "Music" folder.  Most of it moved but I still have about 20 Artist folders in AAC (M4A) Music that Ubuntu refuses to left me move stating I don' have permission.  So...... I sshed into my Ubuntu server and did the following:

```
 sudo su
chown jeremy /mnt/raid 
chmod 777 -R /mnt/raid
```

This should have given my user ownership of EVERYTHING on my RAID.  Then I gave EVERYONE Read/Write permission to the entire RAID.  

However, Ubuntu is still telling me I don't have permission to move or rename AAC (M4A) Music or any subfolders.    I have tried doing this from my Mac via SMB and NFS with the same results.

How can I permanently give EVERYONE full control of my RAID?  This is on my local network and other applications such as XBMC need to be able to read and write to the share.  Thanks for any help sorting this out.

-hogfan

---

### Post by lightningfox on 2011-01-28
Try these commands and see if it works:

```
sudo chown -R jeremy:jeremy /mnt/raid

sudo chmod -R 777 /mnt/raid
```

---

