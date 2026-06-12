---
title: "Installing windows after Ubuntu"
date: 2010-07-28
forum: General Help
---

### Post by xtracool_protik on 2010-07-28
Hey guys,
 I have only Ubuntu on my machine and I'm pretty happy with it, however I wanna play a game so need windows drive. I've blogged about successfully installing windows last year:

[http://heilubuntu.blogspot.com/2009/03/installing-windows-after-ubuntu.html](http://heilubuntu.blogspot.com/2009/03/installing-windows-after-ubuntu.html)

but I'm skeptic about same method since grub is been upgraded.
So I'm curious whether it still works or do i need to take other way round

Thanks

---

### Post by BurningSludge on 2010-07-28
[FONT=Comic Sans MS][SIZE=3]If your game aren't on the [COLOR=Red]bleeding edge[/COLOR] I don't see why you can't try wine first.[/SIZE][/FONT]

---

### Post by ruehara on 2010-07-28
Have you tried using VirtualBox?

---

### Post by xtracool_protik on 2010-07-28
Hey guys thanks for replies,
Sorry for insufficient data:
 I'm trying "Runes of Magic" and its the only game which worked right out of the box on wine. However I've intel graphics card (x3100) and game works one frame at a time its too annoying (I don't know if its because of intel graphics or my ignorance to wine settings).
 I haven't tried virtual box I'll give it a try I hope it shouldn't be a problem at 4GB RAM but I'm skeptic about graphics even then. I'll report back

 And if anyone know better wine configuration please let me know. 
 Some more info:
 Counter Strike in wine works perfect.
 Urban terror, Alien Arena and such works without an issue.
 Heroes of Newerth (even though native linux) needs update from edgers everytime they update client.
 Savage2 (native linux) completely fails.

 I've edgers ppa and use those drivers for intel card

 Thanks again

---

### Post by wilee-nilee on 2010-07-28
> **xtracool_protik said:**
> Hey guys,
 I have only Ubuntu on my machine and I'm pretty happy with it, however I wanna play a game so need windows drive. I've blogged about successfully installing windows last year:

[http://heilubuntu.blogspot.com/2009/03/installing-windows-after-ubuntu.html](http://heilubuntu.blogspot.com/2009/03/installing-windows-after-ubuntu.html)

but I'm skeptic about same method since grub is been upgraded.
So I'm curious whether it still works or do i need to take other way round

Thanks

Here is the link defaulting to reloading grub2 from a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Joe Ker1086 on 2010-07-28
My advice is to install virtual box, install windows (XP preferably) and then install the guest additions so that you can run it in seamless mode. You will barely even notice that you are running windows along side ubuntu :)

PS - awsome avatar haha

---

### Post by xtracool_protik on 2010-07-28
Thanks wilee-nilee that helps (if not now will keep reference for future I'm sure I'll mess up sometime as usual), I have just done installing XP in virtual box. I'll test game and report again.
 Thanks Joe (for Avatar) I've been looking for something like this for a while, I found it on these forums (or some other linux forums, I'll try to recall and have a link for u) only :D

---

### Post by xtracool_protik on 2010-07-29
hmm,
 So Virtual box trial fails for me. As soon as I click on Start Game I get crash report and do I need to send it screen.
 I've assigned 1.8GB RAM to VBox. I didn't install any drivers (not sure if that matters as I can get all resolutions and settings) even if I want to, it fails saying u can't install these drivers. I'll tried drivers from intel's site will try them from dell.
 I tried copying installed game and then I tried new installation - with same result (downloading took so much time :( )

 And Joe I couldn't find Avatar but as much as I recall it was on forum under Avatar pictures subsection, try checking User CP (I couldn't find it though)

Thanks

---

### Post by xtracool_protik on 2010-07-30
Hey thanks again guys,
 anyway dell drivers (which were basically same as intel's on dell site) didn't work as well they just say drivers are not meant for my system :(.
 I changed from 2 Ubuntus to Ubuntu + Windows, thanks to wilee-nilee tutorial worked without any issue :popcorn:
 Ohh yea game is working nice as well on Windows :D (Vista, can't install XP due to AHCI capability :( ) I'll like to try wine version or even VBox but until then will stick to windows plus I get to customize grub2 menu which is awesome :D 
 Thanks again

---

