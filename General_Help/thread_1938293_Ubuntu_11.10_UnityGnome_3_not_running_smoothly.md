---
title: "Ubuntu 11.10 Unity/Gnome 3 not running smoothly"
date: 2012-03-09
forum: General Help
---

### Post by masterman934 on 2012-03-09
Hi there!

I installed Ubuntu yesterday and since then I'm trying to figure out how to fix this problem.

Unity is not running smoothly when I drag windows around, when I minimize them etc... 

I installed Gnome 3 and its running even worse. 

Gnome classic runs alright though but when I enable Compiz Config settings manager by doing [this]("http://askubuntu.com/questions/68711/how-do-i-enable-compiz-in-gnome-classic") everything starts to freeze again and stop begin smooth. 
Also the desktop cube doesn't look like a cube but more like a paper :D

Any ideas of how to fix this? I have installed and enabled fglrx on my System. Graphics card is ATI Mobility Radeon HD 5650.
I don't know if its of any help but I get avg of 32 fps on this test [http://craftymind.com/factory/guimark2/HTML5GamingTest.html](http://craftymind.com/factory/guimark2/HTML5GamingTest.html)

I would appreciate any kind of help!
Thanks!

---

### Post by Carpentr on 2012-03-09
> **masterman934 said:**
> Hi there!

I installed Ubuntu yesterday and since then I'm trying to figure out how to fix this problem.

Unity is not running smoothly when I drag windows around, when I minimize them etc... 

I installed Gnome 3 and its running even worse. 

Gnome classic runs alright though but when I enable Compiz Config settings manager by doing [this]("http://askubuntu.com/questions/68711/how-do-i-enable-compiz-in-gnome-classic") everything starts to freeze again and stop begin smooth. 
Also the desktop cube doesn't look like a cube but more like a paper :D

Any ideas of how to fix this? I have installed and enabled fglrx on my System. Graphics card is ATI Mobility Radeon HD 5650.
I don't know if its of any help but I get avg of 32 fps on this test [http://craftymind.com/factory/guimark2/HTML5GamingTest.html](http://craftymind.com/factory/guimark2/HTML5GamingTest.html)

I would appreciate any kind of help!
Thanks!

I have an ATI 6770 on my Desktop. Whenever I installed the proprietary drivers on my system I would have the same issue. I had to move back to the open-source drivers. Have you tried those?

I've spent days trying to figure it out in Debian to no avail; I believe it is a problem on ATI's end.

---

### Post by masterman934 on 2012-03-09
> **Carpentr said:**
> I have an ATI 6770 on my Desktop. Whenever I installed the proprietary drivers on my system I would have the same issue. I had to move back to the default ones provided by Ubuntu. Have you tried those?

I've spent days trying to figure it out in Debian to no avail;I believe it is a problem on ATI's end.

One of the reasons that I got these fglrx was because Unity was not running smooth so I thought its the ubuntu drivers thats causing this. So I guess thats not the case

---

### Post by Carpentr on 2012-03-09
> **masterman934 said:**
> One of the reasons that I got these fglrx was because Unity was not running smooth so I thought its the ubuntu drivers thats causing this. So I guess thats not the case

I would suggest taking a look at this:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by masterman934 on 2012-03-09
I removed fglrx and everything runs smoothly now. 

Thank you all :)

---

### Post by NikolaSamr on 2012-03-09
ïðîäàæà êîíäèöèîíåðîâ â ìîñêâå - [http://tkf-climat.ru/kondicionery](http://tkf-climat.ru/kondicionery) - ïðîäàæà êîíäèöèîíåðîâ â ìîñêâå

---

### Post by Carpentr on 2012-03-09
> **masterman934 said:**
> I removed fglrx and everything runs smoothly now. 

Thank you all :)

No problem. It is great that it runs smoothly now. It can be annoying when it isn't, for sure.

Have fun!

---

