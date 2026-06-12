---
title: "Big problem with Ati Driver"
date: 2010-11-07
forum: General Help
---

### Post by zmolix on 2010-11-07
Hi there, a friend recomended ubuntu to me saying it's a very good OS.
I was very excited got home and i installed the Ubuntu 10.10 LTS.

( So i am an ubuntu first user [ noob] )

I like it a lot.... but i HAVE A BIG PROBLEM with my Ati sapphire x1550 on a DELL E772p 17"
When i try to change my resolution it says that 1152 x 864 is the biggest, and reads my monitor as a 15" ![IMG]http://img121.imageshack.us/img121/6905/bigproblem.png[/IMG]

So i started searching on youtube a lot of tutorials, did not help.
I started searching on google and try a lot of tutorials from Ubuntu Forums did not help.
I installed a lot of ATI drivers from the Synaptic Package Manager for 
I used some commands in the terminal, all from this forum.
I follow all the tutorials step by step.

I installed the Ati Catalyst control center and when i click it 

*"  There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.* p, li { white-space: pre-wrap; }  *No ATI graphics driver is installed, or the ATI driver is not functioning properly.*
 *Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."*


Please can one of you who better know linux hepl me ?
But please do it Step by step, i'm not a morron but i don't know the terminal commands and linux terms so well.

P.S. My friend has the same monitor same video card but a oldder ubuntu, he did not have the problem,
P.S. 2 Sorry for my bad english !

---

### Post by Yellow Pasque on 2010-11-07
Don't install Catalyst. Your card is unsupported and you only screwed up your install by doing that. Follow this to reset the driver: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver) and next time, try to do a quick google and follow directions.

---

### Post by 3Miro on 2010-11-07
ATI and Linux often don't like each other. This is especially true for older ATI cards. ATI used to have no support for Linux, ever since AMD took over, there have been huge improvements, however, ATI is still not at the same level as Intel and Nvidia. This should change soon with the new FOSS ATI drivers, but those will cover only the newest video cards.

---

