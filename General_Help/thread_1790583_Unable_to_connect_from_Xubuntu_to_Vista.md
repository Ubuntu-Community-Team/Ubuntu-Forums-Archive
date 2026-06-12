---
title: "Unable to connect from Xubuntu to Vista"
date: 2011-06-25
forum: General Help
---

### Post by yakmag on 2011-06-25
Hullo,

I've recently installed Xubuntu and now struggling to get my vista pc and laptop to connect to each other.

I can ping my laptop from my vista pc.
From my laptop I can run Gigolo and see my shared folders on my vista pc, when I try to connect I get the following error...

Failed to open "smb://main/downloads/".
The URI "smb://main/downloads/" is invalid

On my vista pc I can see my laptop and connect to it, however the only thing I can see shared are the printers folder.

I have managed to connect to my printer (shared via my network router) and can print from this ok.

Could anyone help with my other issue please?

Obliged in advance!

---

### Post by Toz on 2011-06-25
> **yakmag said:**
> Hullo,

I've recently installed Xubuntu and now struggling to get my vista pc and laptop to connect to each other.

I can ping my laptop from my vista pc.
From my laptop I can run Gigolo and see my shared folders on my vista pc, when I try to connect I get the following error...

Failed to open "smb://main/downloads/".
The URI "smb://main/downloads/" is invalid
I don't personally mount Windows shares, but on gigolo's web page, there are some instructions to follow (esp. make sure you have gvfs-fuse and fuse-utils installed). See: [http://www.uvena.de/gigolo/help.html#open-resources-in-thunar-on-xfce-4-4-and-4-6]("http://www.uvena.de/gigolo/help.html#open-resources-in-thunar-on-xfce-4-4-and-4-6"). I know the reference is for 4.4 & 4.6, but it might be helpful nonetheless.


> On my vista pc I can see my laptop and connect to it, however the only thing I can see shared are the printers folder.

I have managed to connect to my printer (shared via my network router) and can print from this ok.

Could anyone help with my other issue please?
To connect to Xubuntu shares you need to have **samba** installed on xubuntu - (from the command line)```
sudo apt-get install samba
```(or search for Samba in the software centre), and you'll need to edit a file - **/etc/samba/smb.conf**. Have a look at the documentation here: [https://help.ubuntu.com/community/Samba/SambaServerGuide#Samba%20Server%20Configuration%20-%20Manual]("https://help.ubuntu.com/community/Samba/SambaServerGuide#Samba%20Server%20Configuration%20-%20Manual") for more detailed information and instructions.

---

### Post by yakmag on 2011-06-26
Cheers Toz!!

It was the install of Samba which I was lacking.

Now can connect from Vista to Xubuntu!

Cheers!!

Richie

---

### Post by Toz on 2011-06-26
Great. Can you please mark this thread solved?

---

