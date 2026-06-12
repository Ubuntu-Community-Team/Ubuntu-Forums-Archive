---
title: "Totaly lost"
date: 2010-05-18
forum: General Help
---

### Post by Xavierdri on 2010-05-18
Hi to you all

Could some one please tell me where is the new user introduction? as I would like to introduce my self but after looking for some time now I finally gave up and to make matters worst  I went to the Ubuntu help but did not find any :confused: I'm really having a bad day. :(

Regards Xavier

---

### Post by Chesamo on 2010-05-18
That's quite the request. Did you try the wiki?
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
Or perhaps the Ubuntu Beginners Team can help you out?
[https://wiki.ubuntu.com/BeginnersTeam](https://wiki.ubuntu.com/BeginnersTeam)

---

### Post by cascade9 on 2010-05-18
With "Active Members: 66,449" introduction theads are kind of pointless IMO. You might as well just dive in (well, you've done that now anyway ;) ) There is at least one around though- 

[http://ubuntuforums.org/showthread.php?t=1451097&highlight=introduce](http://ubuntuforums.org/showthread.php?t=1451097&highlight=introduce)

What sort of help were you looking for?

---

### Post by Xavierdri on 2010-05-18
Well let's just say that I have not got the fantiest idea of how to use Ubuntu (the friendly one) I cant even get to load a bit of software when I try to do like in the instructions that I got with the software WELL I type the instruction in the terminal window but nothing so I try again and still nothing and at the end of the day if i cant come right I will be forced to put windows back on or I just wont be able to do my work surely it cant be that difficult to load some soft? I must have Diptrace for my PCB design and I need to write code for my Pic's and I must programme the pic  other than that all is OK :P

---

### Post by Dkkline on 2010-05-18
Well could you give a bit more information?What's Diptrace? Windows software?Anyway if so you might try open a terminal and type something like ```
sudo apt-get install -y wine
``` (wine is a program that emulates(ops sorry does emulate windows, sorry cascade9 my mistake :S) windows) then type ```
wine <path/to/diptrace/diptrace-launcher.exe
``` I've have no idea if this will help you or not.

Hope you stay Ubuntu (you could also try duel-booting?), and get your problem solved

---

### Post by cascade9 on 2010-05-18
A bit more info would be good. What commands were you entering? What happened? 

As far as diptrace goes, you will need to run it with WINE (Windows In a *Nix Enviroment, or WINE IS Not an Emulator). The diptrace website even mentions WINE- 

> Compatible with **Windows NT/2000/XP/Vista/7, Linux(Wine)**; Windows 9x/ME are not recommended.

[http://www.diptrace.com/download.php](http://www.diptrace.com/download.php)

Seems to be very good in WINE from the WineHQ site- 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6668](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6668)

---

### Post by oldfred on 2010-05-18
Are you looking for more info:

Beginnners guide:
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
Ubuntu Documentation:
[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)

[http://ranjith.zfs.in/ubuntu-10-04-lucid-lynx-post-installation-guide/](http://ranjith.zfs.in/ubuntu-10-04-lucid-lynx-post-installation-guide/)

---

### Post by rnerwein on 2010-05-18
> **Xavierdri said:**
> Hi to you all

Could some one please tell me where is the new user introduction? as I would like to introduce my self but after looking for some time now I finally gave up and to make matters worst  I went to the Ubuntu help but did not find any :confused: I'm really having a bad day. :(

Regards Xavier

hi
you know google ???
ciao

---

### Post by Megaptera on 2010-05-18
> **rnerwein said:**
> hi
you know google ???
ciao

 Hi rnerwein,
You know Forum Guide?:confused: 
Quote"RTFM, "Go look on google" are two inappropriate responses to a question. If you don't know the answer or don't wish to help, please say nothing instead of brushing off someone's question."

Please remember we were all new to Ubuntu at some stage.

Thanks.:)

---

### Post by bigsmitty64 on 2010-05-18
Welcome to the forums. I know the software you mentioned is a windows based software and wine is the way to go there, BUT, keep in mind that in Ubuntu you can use the Software center, "applications/Software Center", to find (and install) thousands of software titles very easily. Most are just click and install. I find little need to surf the web anymore looking for software.
There is also Synaptic Package manager, a little trickier to get used to but not bad at all.
You type in what you want, if it's there, you click, mark for instulation, and the hit the apply button. Linux can be tricky for new users, but once you get the basics down, you'll find that it's unbelievably, fun and easy! Good luck and have fun!

---

### Post by Xavierdri on 2010-05-18
Ok well so many answers and questions that I'm not to sure where to start Ho but first Rnerwein :) 
 That having being said when you sent a quick reply what link are you supposed to click on or dose it not matter? Ok I did download WINE but how do I install it I read the Readme text file and it looks like I have to install other files too to run it.

---

### Post by cascade9 on 2010-05-18
Well, that is doing things the hard way. It is possible to download programs and then install then (like you do with windows) but its much easier to use synaptic, or the software centre. Search for WINE, find the packages in the list, and install it from there. 

Thats one of the good things about having software repositories- you dont have to hunt around the interent to find the vast majority of software, or worry about getting corrupted or hacked exe/msi files.

---

### Post by Xavierdri on 2010-05-19
Hi Cascade9

Firstly I must thank you for the link I downloaded the E-Book and found it to be just what I needed it's only been 72 hours that I have Linux and I'm loving it already. As for the software that is ready for download I did not find what I needed I did download a PCB and schematic package but I don't find it at all friendly mind you it was developed by a French man and why make things easy when you can make them difficult any how I had downloaded Wine before I changed operating system and placed it with all the other software that I found that was Linux compatible on a CD thinking that I would simply install it like you do on Windows Ha Ha well no sir hence the start of all my problems and the solution was quite simple up till now all that I had to do was change directory got to my software that I downloaded type ./configure then just sit back and wait for it to tell me what are the missing drivers I am however having problems with a short cut that just will not work but I'll bug you with that latter.

Regards Xavier

---

### Post by the8thstar on 2010-05-19
> **Xavierdri said:**
> ...I don't find it at all friendly mind you it was developed by a French man and why make things easy when you can make them difficult

Hey wait a minute here! What is that supposed to mean? :)

---

### Post by Xavierdri on 2010-05-19
I come from Belgium and I know that if it can be done the hard way then that's the way we do it and in France it's the same hell why do you think I live in South Africa :P I work in the printing industry so I did a lot of travelling in Africa and Europe man you guys over there stress to much man and always doing thing the hard way. Hey hope that you wont take this badly 

Regards Xavier

---

