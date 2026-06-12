---
title: "New to the board, question about add/remove"
date: 2010-08-07
forum: General Help
---

### Post by sarus86 on 2010-08-07
ok so im new to the board and new to the world of ubuntu, i recently installed ubuntu 10.04 on a virtual machine, but so im trying to find my add/remove under applications and its not there and when i go to the main menu its not even an option to have.  Is something messed up or how can i find it? the help is greatly appreciated

---

### Post by surfer on 2010-08-07
try
Applications -> Ubuntu Software Center
or
System -> Administration -> Synaptic Package Manager

---

### Post by sarus86 on 2010-08-07
ok well i checked those 2 and im confused because i cant find anything about add/remove.  See what im trying to do is get to Advanced Display Options but from what i have read on this forum is that to get that you have to go to add/remove programs and install that first, but i cant get to add/remove programs so i want to be able to have that application.

---

### Post by Quarkrad on 2010-08-07
There is not a windows type add/remove in Ubuntu. This is a method of removing,for example, firefox:  Go System/Admin/Synaptic Package Manager - at the top of the window type in firefox and hit Return or Search.  Synaptic will find all instances of firefox on your machine - the version you are using has a green box against it (as well as all other associated files for that version of firefox).  If you right click on the word firefox you will have options to remove the package.  (I would not suggest you remove it unless you have backed up all you need (e.g Bookmarks).  The other method (I use as a newbie) is Applications/Ubuntu Software Centre.  If you type in firefox you should see a list of apps - the top one will have a little green tick against it -indicating it is installed on your PC.  There is a Remove button to get rid of it.

---

### Post by sarus86 on 2010-08-07
Quarkrad from what i have found from the forum is that in older versions of ubuntu there definitely was an add/remove applications, im just curious if there is one for the newest version because i need that to activate the advanced desktop settings

---

### Post by Vaphell on 2010-08-07
what these advanced desktop settings are supposed to do? do you think about compiz effects or what?

---

### Post by sarus86 on 2010-08-08
Ok well this is what im trying to do, first i installed ubuntu on my virtualbox, then i started reading about some cool things ubuntu has like the "desktop cube" so basically now i want to get the cube to work, from what i have read i installed both ccsm and simple ccsm and i have changed the settings instide of those to allow "desktop cube" but from what i have read i have to go into appearance then visual effects then change that from "none" to "custom" but when i do that it gives me a message that it can't and i believe it is from my virtual machine not using my video card driver properly but i dont know how to change that so i am working on that now

---

### Post by Vaphell on 2010-08-08
rightclick on desktop, choose last option (change background?) and ther one of the tabs is responsible for the level of eyecandy (none, some, full)
the same stuff is available from System->Prefs->Appearance

---

### Post by sarus86 on 2010-08-08
ya and when i click on the custom one it says searching for drivers then eventually comes up with a message stating "Desktop effects could not be enabled"  from what i have read it is because of my video driver, because i am using a virtual box it didnt recognize my driver in my pc it is using the driver on the virtual box but i dont kno how to change that

---

### Post by Quarkrad on 2010-08-08
I'm a bit limited here  I have not used Ubuntu via Virtualbox - only natively.  I have only used Software Centre/Synaptic/Terminal to add/remove apps.

---

### Post by Vaphell on 2010-08-08
oh, i forgot you use virtualboxed ubuntu. Getting 3d acceleration in guest system is not trivial, i had my share of problems with embedded xp. Have you installed guest additions?

[http://tombuntu.com/index.php/2009/04/08/3d-acceleration-and-compiz-inside-virtualbox-guests/](http://tombuntu.com/index.php/2009/04/08/3d-acceleration-and-compiz-inside-virtualbox-guests/)

---

### Post by sarus86 on 2010-08-08
ok well thanks for the help anyway, ill c what i can find out on my own

---

### Post by sarus86 on 2010-08-08
ok well i tried to fallow the link u gave me im just not understanding the shared folder part, like what is that part for?

---

