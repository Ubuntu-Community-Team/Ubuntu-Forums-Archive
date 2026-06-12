---
title: "Change NTFS file permissions from Ubuntu"
date: 2010-03-07
forum: General Help
---

### Post by seece on 2010-03-07
Hi!

I tried searching with my problem but there was not any working solutions so I'm starting a new thread here. So I tried to share a folder to my local network on my Windows XP installation but it ended up locking me - the administrator - out of the folder I was trying to share. I can't access the folder from Windows or alter it's permissions because it only states "Access denied.". The folder is lying on my external harddisk which is formatted in NTFS.

I also tried changing file permissions on other machine running Windows but it doesn't allow me to access it either. I can mount the drive on my Ubuntu easily and access all the files and folders, but I don't how to edit file permissions set by Windows.

Copying the files from the folder to another place and deleting the original didn't help because every file in it has it's own permissions :P

So how can I edit these permissions with Ubuntu? Chmod doesn't help.

---

### Post by blueridgedog on 2010-03-07
You can not edit NTFS permission from within Ubunutu.  

Can you log in as "administrator" to the windows PC and then take ownersip of the files?

In windows, Right click directory, properties, security tab, then advanced, then owner tab.

---

### Post by Wanas on 2010-04-16
> **blueridgedog said:**
> You can not edit NTFS permission from withing Ubunutu.  

Can you log in as "administrator" to the windows PC and then take ownersip of the files?

In windows, Right click directory, properties, security tab, then advanced, then owner tab.

I have gone to the place you said (... then the owner tab) what should I do next, there is two users there but I cant delete any of them ?
Here a screen shot of what I got in the tab

---

