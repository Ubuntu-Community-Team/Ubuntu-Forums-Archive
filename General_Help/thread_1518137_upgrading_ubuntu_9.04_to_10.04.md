---
title: "upgrading ubuntu 9.04 to 10.04"
date: 2010-06-26
forum: General Help
---

### Post by abhishek_sharma on 2010-06-26
i am trying to upgrade my ubuntu from the installation cd but not sure about whether the data in the harddrive partions will persist or not???

will the installed plugins and softwares will remain???

---

### Post by Spr0k3t on 2010-06-26
Not really sure what you have installed or configured etc. but I would seriously recommend making a backup of your /home/* and be prepared to accept a clean install.  You could test it out by making a virtual machine with 9.04 configured to your specifics and performing an upgrade in the virtual machine to see the outcome.  From my personal experience of upgrades from prior revisions to current... clean install of 9.10 to 10.04 wasn't that big of a deal.  The problems occured when I upgraded from prior to 10.04.  Some issues were minor and dependant on the chipset of the machine.  Other issues required a bit more research with hardware levels until someone posted a fix (but that was a problem even with a clean install).

What I would do though... read through the sticky at the top and see if there might be anything related to your setup in the thread.  You never know what you might find.

---

### Post by okplayer02 on 2010-06-26
> **abhishek_sharma said:**
> i am trying to upgrade my ubuntu from the installation cd but not sure about whether the data in the harddrive partions will persist or not???

will the installed plugins and softwares will remain???



depends if for example you installed your /home partition as a seperate partition if you did then yes you can have your data after you upgraded if not then everything will be wiped clean. so like the previous poster stated backup your data in your home partition. 

next you can not upgrade directly from 9.04 to 10.04 you must 
 
9.04 ----> 9.10 -------> 10.04 
so its easier just to do a clean install

---

### Post by abhishek_sharma on 2010-07-01
> **okplayer02 said:**
> depends if for example you installed your /home partition as a seperate partition if you did then yes you can have your data after you upgraded if not then everything will be wiped clean. so like the previous poster stated backup your data in your home partition. 

next you can not upgrade directly from 9.04 to 10.04 you must 
 
9.04 ----> 9.10 -------> 10.04 
so its easier just to do a clean install


thankz.......
it was easier n better to make a clean install.

---

