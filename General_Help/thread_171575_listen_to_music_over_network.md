---
title: "listen to music over network"
date: 2006-05-06
forum: General Help
---

### Post by tronica on 2006-05-06
I found that i should use this to mount a windows share to be able to listen to my music with out having to drag the files localy. 

> mount -t smbfs //servername/sharename /path/to/mount -o username=windows_username,password=windows_password

but i'm not sure what i should put in the /path/to/mount

can someone point me in the right direction. Thanks

---

### Post by ZylGadis on 2006-05-07
You need to substitute it with the full path to an empty directory somewhere on your linux tree. A good place is /media:

sudo mkdir /media/windowsmount

That will create the directory. Use /media/windowsmount up there, and it should run fine. After mounting, it should show up on your desktop as a new drive; or, you can simply go to /media/windowsmount in nautilus or a terminal, and you'll have your mounted windows things there.
I'm not sure what permissions you would need, though, as I don't use samba. In case you run into permission troubles, change the ownership of your new directory (preferably before mounting):

sudo chown myusername /media/windowsmount

Hope that helps.

---

### Post by anthro398 on 2006-05-07
If I'm not mistaken, /mnt is the directory into which mount points should be placed.  Do it anywhere you like, though.

---

### Post by kupajava on 2006-05-08
Three points here.

1. If you are mounting to a share on a win2k3, use "cifs" instead of "smbfs" to prevent a problem where the share becomes a file you cannot open.

2. If you mounted to say /media/music you would then have a desktop icon that goes directly to that share.  If you instead use /mnt/music you wouldn't have the desktop icon, thats the only difference and is the reason that some choose /media or /mnt.

3. Remember, you will have to of course create the folder first (you probably knew this) and then set the permissions to, oh lets say, 777 or 755 so that you can work with the share once it is created.  Forgetting to set those permissions will give you a world of hurt...

---

