---
title: "No read Emblems"
date: 2009-07-16
forum: General Help
---

### Post by Kalamata on 2009-07-16
Hello,
 
I just install Ubuntu on my IBM R51 laptop and I am trying to get the Sierra Wireless AC875 card to work on it. Since I work for a wireless company her in the US I have additional support article to create the scripts for the modem and communication with the wireless device. My problem is that I have files and folders that have a No Read emblem on it. Those files and folders do not allow me to view, write, copy or paste anything into them and it remains searching.
 
The error message read as follow: 
 
"The folder contents could not be displayed." You do not hve the premissions necessary to view contents of "Peers"
 
And I am the only user and administrator on this computer.

---

### Post by TeoBigusGeekus on 2009-07-16
```
sudo gedit /location/of/file/nameoffile
```
Give your password and you can edit any file you want.

---

### Post by Kalamata on 2009-07-16
Hello TeoBigusGeekus,
 
Thank you for the code, but since I can't see the file in the peers folder I don't know their name to modify them. I am trying to drag and drop some files on the peers folder and I am not allow to do that either. 
 
Kalamata...

---

### Post by TeoBigusGeekus on 2009-07-16
Ok re patrida.
```
gksudo nautilus
```
It will open nautilus with root priviledges and you will be able to do anything.

---

