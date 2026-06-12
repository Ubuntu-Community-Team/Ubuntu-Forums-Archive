---
title: "how can i access the Windows Share folders from linux?"
date: 2010-03-29
forum: General Help
---

### Post by eival on 2010-03-29
i want to have full read/write control to be able to drag and drop files to those folders from my linux computer over my network and i want that folder to also be accessable to anyone on the network

basically i need to do the exact opposite of creating the share folder with samba in linux an then mapping the network drive in windows. which allows me to access the linux folders from windows, but i want the folder to be hosted on windows.

but i dont know the terminal codes to do that and the Network and Network Tools in "System>Admin" dont seem to offer this support

---

### Post by eival on 2010-03-31
bump, does anyone know?

---

### Post by NovaWasp on 2010-03-31
```
smbmount //computerOrIP/sharedFolder mountFolder/ -o user=[username]
```
 
You'll be promted for the password. In an Active Directory enviornment where the work group is something like corp1, the user name will be corp1\username in windows. Linux needs corp1\\username in the command line.
 
If you're connecting to folder Music on Machine music-box with user name jimmi.
 
```
 mkdir musicMnt
smbmount //music-box/Music musicMnt/ -o user=jimmi

```
 
Hope that helps.

---

### Post by Iowan on 2010-03-31
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a GREAT How-To for Windows sharing problems.

---

