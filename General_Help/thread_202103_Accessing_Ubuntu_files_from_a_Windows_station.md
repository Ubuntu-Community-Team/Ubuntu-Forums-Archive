---
title: "Accessing Ubuntu files from a Windows station"
date: 2006-06-22
forum: General Help
---

### Post by kmartin on 2006-06-22
Just as the title says, I want to enable file sharing between the two computers. Right now I can access the files on the Windows machine from the Ubuntu system but I cannot do vice-versa..

From what i'm seeing, do I install samba and then configure that to share files?

Enlighten me :)

---

### Post by TheMono on 2006-06-22
Install samba and then configure that to share files.

lol.

Using synaptic, just search for samba, install it.

Right click on the folder you want to share, click Share folder, 

Select Share with SMB, give it a name, and mess round with other settings accordingly.

---

### Post by kmartin on 2006-06-22
[QUOTE=TheMono]Install samba and then configure that to share files.

lol.

Using synaptic, just search for samba, install it.

Right click on the folder you want to share, click Share folder, 

Select Share with SMB, give it a name, and mess round with other settings accordingly.[/QUOTE]

no need to lol... I was just double checking

---

### Post by x64Jimbo on 2006-06-22
[QUOTE=kmartin]no need to lol... I was just double checking[/QUOTE]
Yeah, seriously. Is that what you think is being helpful? Laughing at kmartin? Spare the lol next time.

---

### Post by msak007 on 2006-06-22
I haven't booted into Windows for months, but when I used to I used [Ext2 IFS]("http://www.fs-driver.org/"). Once you install it, it adds a Control Panel applet that lets you assign drive letters to your ext2/3 hard drive / partitions so you can see them and transfer files to / from them in Windows.

---

### Post by nix4me on 2006-06-22
samba shares work nicely once configured correctly also.

nix4me

---

### Post by PhairOh on 2006-06-22
kmartin, how did you get it so that you can access the files on the Windows machine from the Ubuntu system?  I've been trying to get that working for some time but cannot figure it out.

---

### Post by beerorkid on 2006-06-23
well if you have shared folders on the windows machine you can see the files by:
places --> network servers

or get nautilus open, gonna need the location bar, and hit it by ip address
smb://192.168.1.100

might need smbclient

---

