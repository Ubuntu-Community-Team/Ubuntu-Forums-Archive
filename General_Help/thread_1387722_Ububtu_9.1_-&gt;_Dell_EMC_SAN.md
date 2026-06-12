---
title: "Ububtu 9.1 -&gt; Dell EMC SAN"
date: 2010-01-22
forum: General Help
---

### Post by AndrewWood on 2010-01-22
I find myself in unfamiliar territory. I am attempting to get a Dell M610 (in an M100e) running Ubuntu 9.1 64bit to talk to a Dell EMC Fibre Channel Array. The Dell has an Emulex card in it and it appears that the driver is loaded OK.

What I am not sure on is what to do next! I have the SAN end configured but how do I get my LUN mounted on Ubuntu ?

Thanks
Woody

---

### Post by zaphod777 on 2010-01-22
If you have everything on the EMC and the switch configured proerly you should be able to use GPARTED to format the LUN just like another HDD would be on your machine. 

Are you running a Server version or a Desktop version of ubuntu?

Here is a tutorial for mounting a drive in Server edition
[http://www.ghacks.net/2009/09/10/add-a-second-drive-to-your-ubuntu-server/](http://www.ghacks.net/2009/09/10/add-a-second-drive-to-your-ubuntu-server/)

IF you have zoned the switch properly then you should be able to follow that tutorial since it is basically the same as a physically connected HDD. 

Assuming that the EMC side is done right. I have worked with SANS before in Windows so I might be able to help there.

---

