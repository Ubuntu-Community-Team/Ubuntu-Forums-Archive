---
title: "How to share a folder in ubuntu"
date: 2009-12-15
forum: General Help
---

### Post by alfphie on 2009-12-15
How do i share a folder in ubuntu in oder to be shared in a LAN!

---

### Post by philinux on 2009-12-15
Right click on folder> Sharing options.

---

### Post by Alex Libman on 2009-12-15
Just right-click on a folder (ex. in [Nautilus]("http://en.wikipedia.org/wiki/Nautilus_%28file_manager%29")), select "Properties" in the pop-up menu, click the "Sharing" tab, check the "Share this folder" checkbox, edit the share name if needed, and click "Create Share".

You may be asked to enter your password and then restart your system if you don't have the required [Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29") components already installed.

---

### Post by tylersontag on 2009-12-15
do you know why another ubuntu box (both 9.10) on the network would not be able to see the other machine?

i have 2 boxes, each sharing a folder and neither one can see the other box under Places>Network, though each can see itself.

---

### Post by Iowan on 2009-12-15
[https://help.ubuntu.com/8.10/internet/C/networking-shares.html]("https://help.ubuntu.com/8.10/internet/C/networking-shares.html")
(based on 8.10)

tylersontag:
Using Samba (Windows share)? [This]("http://ubuntuforums.org/showthread.php?t=1169149") may have some suggestions.

---

### Post by tylersontag on 2009-12-16
I had to turn on "allow guests" since it defaulted to a smb sharing...  I suppose thats fine, even though i dont have any windows boxes in my house... maybe a friend will want to do some networking, i dunno.

 Thanks!   Though on another note, i don't know if my router's really slow, but im usually getting about 600kB/s traffic over my wireless router, this sound slow to your guys?  Heck i DL faster than that sometimes!

---

