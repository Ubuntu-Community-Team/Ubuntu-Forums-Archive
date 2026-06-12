---
title: "Mapping a Network shared drive"
date: 2011-12-17
forum: General Help
---

### Post by Herbon on 2011-12-17
[FONT=Garamond][SIZE=3]I have a Network drive (Stora) which I would like to map to the desktop of my Linux box.

Using the following link
[http://talkingtek.com/map-drive](http://talkingtek.com/map-drive)

I attempted to edit the /etc/fstab, with 

[/SIZE][/FONT]> [FONT=Garamond][SIZE=3]//windows-server/share-folder  //media/sharename cifs  credential=/home/users[/SIZE][/FONT]
[FONT=Garamond][SIZE=3]
[/SIZE][/FONT]
[FONT=Garamond][SIZE=3]/.smbcredents,iocharset=utf8,file_mode=0777,dir_mode=0777  00[/SIZE][/FONT]
[FONT=Garamond][SIZE=3]
[/SIZE][/FONT][FONT=Garamond][SIZE=3]

When I try to save it I get the following error.

[/SIZE][/FONT]> [FONT=Garamond][SIZE=3]E486: Pattern not found: windows share[/SIZE][/FONT][FONT=Garamond][SIZE=3]

Should I add dev/???? before windows share??? or drink more beer?


Thanks in advance[/SIZE][/FONT]

---

### Post by Paqman on 2011-12-17
You need to change //windows-server/share-folder/ to the actual location of your share. You'll also need to change /media/sharename to be the actual folder on your machine that you want to mount the share on.

---

### Post by Herbon on 2011-12-17
> **Paqman said:**
> You need to change //windows-server/share-folder/ to the actual location of your share. You'll also need to change /media/sharename to be the actual folder on your machine that you want to mount the share on.


:confused:[FONT=Garamond][SIZE=3]

So example would be..........[/SIZE][/FONT]

>  //10.10.2.4/Mylibrary/Network_Media_Audio/[FONT=Garamond][SIZE=3]sharename cifs  credential=/home/users[/SIZE][/FONT]

---

### Post by Herbon on 2011-12-18
bump

---

### Post by Paqman on 2011-12-22
Almost, try something like:

```

//10.10.2.4/Mylibrary/Network_Media_Audio/ **/media/sharename** cifs credential=/home/users/.smbcredents,iocharset=utf8,file_mode=0777,dir_mod e=0777 0 0

```

You'd also need to change the bit in bold to be the actual location on your machine where you wanted to mount that share. So for example if you wanted it to show up at /media/Audio you'd make a folder in media called Audio by doing:
```
sudo mkdir /media/Audio
```
The your line in /etc/fstab would become:

```

//10.10.2.4/Mylibrary/Network_Media_Audio/ /media/Audio cifs credential=/home/users/.smbcredents,iocharset=utf8,file_mode=0777,dir_mod e=0777 0 0

```

Anything mounted in /media will show up as a removable drive on your desktop. If you don't want that just mount it to a folder in /mnt instead. 

Also, make sure that the address of your share on the network (10.10.2.4) is static. If your router assigns addresses dynamically using DHCP (which is the default behaviour) then you'll have to go into its settings and tell it to always assign that address to that machine instead.

---

