---
title: "Which version to use for a Media Server?"
date: 2006-06-05
forum: General Help
---

### Post by hfwarner3 on 2006-06-05
I am currently running Windows on a 2.4 Ghz Celeron Dell 2400 PC with 512 MB of RAM and two drives (80 GB and 200 GB).  We use it as our family file server and our media server.  It holds all our documents, our music (WMA and MP3), our digitial photos, our home movies, and stores TiVo shows that we want to keep long term.  It interfaces with the TiVo through Galleon.

We have 3 other PCs in the house and I have upgraded one of the children's PCs from Windows 98 to edubuntu 6.06.  The kids picked up the interface quickly and love the apps and games I installed.  

Since I have decided to take the linux plunge and have chosen ubuntu as my distro, I am looking for some general advice on picking flavors.  

I want to upgrade the media/file server to ubuntu and it seems to me that using the server ubuntu distro would make sense until we get to Galleon.  It needs Java (easy enough), but the interface I use on windows is a GUI.  Should I consider going to xubuntu instead so I have a desktop to work with? 

The other PC the kids have is a eMachines 466id (466 Celeron) running Windows 98.  It has all their games on it (Reader Rabbit, Zoombinis, Jumpstart Learning, etc.).  Given the hardware they have to work with, is it worth trying to move them to edubuntu and get the games running under WINE?  I know nothing about WINE and have heard some nightmare stories.  

Thanks in advance for your advice!

---

### Post by onesojourner on 2006-06-05
[QUOTE=hfwarner3]  It needs Java (easy enough), but the interface I use on windows is a GUI.  Should I consider going to xubuntu instead so I have a desktop to work with? 
[/QUOTE]

ubuntu edubuntu xubuntu and kubuntu are gui distros. I went with ubuntu. xubuntu is supposed to be lightweight, any should be fine. it seems most how tos are written for ubuntu so thats what I picked when I decided.

---

### Post by hfwarner3 on 2006-06-05
ubuntu DESKTOP is a gui distro, but the SERVER is not, right?

---

### Post by SSTwinrova on 2006-06-05
[QUOTE=hfwarner3]ubuntu DESKTOP is a gui distro, but the SERVER is not, right?[/QUOTE]
I don't believe the server edition comes with a GUI by default, but you could add one at a later time if you wished.

---

### Post by hfwarner3 on 2006-06-07
[QUOTE=SSTwinrova]I don't believe the server edition comes with a GUI by default, but you could add one at a later time if you wished.[/QUOTE]

So, if you install the Java DRE on a system without a GUI, what happens when you run a Java app that has a GUI?  Does it work or not?

---

### Post by xtacocorex on 2006-06-07
[quote="hfwarner3"]So, if you install the Java DRE on a system without a GUI, what happens when you run a Java app that has a GUI? Does it work or not?[/quote]

It would not work if there is no X-Server running, but it would work if it didn't need the GUI to function properly, there might be an option to run it command line only or something of that nature.

---

### Post by hfwarner3 on 2006-06-07
OK, I am going to try it with xubuntu.

---

### Post by carlosqueso on 2006-06-07
I have basicly the same setup as you (with the exception of TiVo) and have a ubuntu server setup with the xubuntu-desktop and icewm packages for GUI.   It works just fine, although you will need to use samba instead of NFS (like me) if you don't convert the kids' computer.

---

