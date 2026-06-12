---
title: "sysctl.conf settings to use ram more effectively"
date: 2009-06-30
forum: General Help
---

### Post by eelfner on 2009-06-30
I am trying to tune my Ubuntu system to more effectively use the 2GB of Ram I have. I realize that there are many posts regarding this, but wondered if my situation is somehow different. I can **never** get more than 1GB of my Ram (as viewed in System Monitor) utilized. I currently have a 1GB swap, and it will go up to 75% used. And I see lots of swap activity.

_sysctl.conf additions_
vm.overcommit_memory = 1       
vm.overcommit_ratio = 50           
vm.swappiness = 1               
vm.dirty_ratio = 60     
vm.dirty_background_ratio = 1       

The big memory players are VMWare with (768MB allocated - running a Win2K3 server). Eclispe IDE. SQL Developer (java program). Tomcat (java app). Plus Firefox, etc.

I'm thinking maybe I need to increase the vm.overcommit_ratio, but am getting tired of fishing and hoping someone can put the fish on my line for me.

TIA - Eric

---

### Post by AoSteve on 2009-06-30
VMWare is eating a LOT of that ram.   Compiz usually adds a bunch on with a lot of effects turned on.   I also noticed AWN eats up about 80mb on this laptop at normal use with 8 icons on it....

I disabled a lot of compiz and switched to a single gnome panel and dropped total use to 410m with zero swappage.    I have 2gb of ram though...     I don't know if you'll be able to cut it to where you won't use swap if your running 768mb for the VM box.

---

