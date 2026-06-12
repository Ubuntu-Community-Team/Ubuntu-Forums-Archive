---
title: "Ubuntu install with windows"
date: 2006-02-06
forum: General Help
---

### Post by Nitrous570 on 2006-02-06
Hey there,

At the moment I am running windows xp home edition on my old comp. Due to the lack of speed that I am experiencing, and the fact that I am interested in Ubuntu, I am going to dual boot (because my parents do not have much computer xperience). So my question is is how do I, during the installation, still keep windows and install ubuntu, at the same time. How do I make a partition (and what size) during the install of ubuntu. :confused: At the time of the windows installation, we did not make a partition (did not think about switching to linux that much, until i heard of the ease of ubuntu) and that is what is allowing me to switch. Good job Ubuntu. So ya some questions I have. 

On the system I am installing ubuntu:
1) i need video drivers for a nvidia geoforce 2 mx card
     -Where do I get them if I am installing the 32-bit version of Ubuntu. 

On the system of mine that I want to swithch also, but the live cd does not seem to work (Says that my cd drive might be currupt, but that does not make sense to me..cause it does work perfectly in windows....maybe I should check to be sure... ne one else get this error?) 

1) It has a x800xl 512mb video card, where do i get drivers for it... and how. Do I go to the ati site.. heard that is not good, or do I put in a code in the terminal/kernel thingy. 
2) i have a nvidia A8N-E mobo, where do I get drivers for that..the actual nvidia site(which one). 

Thx guys this really helps me out. I am new..well that is obvious, thx for ur help. It is nice to have people to help me out. :mrgreen:

---

### Post by snellgrove on 2006-02-06
Sounds like you may have (when installing XP originally) set XP to use all of the available disk space (it does this by default)

So to install Ubuntu, you will need to wipe the PC, and setup XP with say 50% of the hard drive space used, and then just go and install Ubuntu - ubuntu will know XP is installed, and use a menu when you turn the PC on called 'Grub' which will let you choose between XP and Ubuntu (it'll default to Ubuntu though, you may want to make your parents aware)

Geforce drivers are easy enough, there'll be a guide on here somewhere (probably more than one) - you can install a driver through "synaptic package manager" which involves putting a tick in the box and hitting apply - driver installed! :D

My Live CD died as well, burnt another and it was fine :) who knows with this one though, try it in another PC to check if its the CD or a hardware incompatibility with your PC

---

### Post by lha on 2006-02-06
[QUOTE=Nitrous570]Hey there,

At the moment I am running windows xp home edition on my old comp. Due to the lack of speed that I am experiencing, and the fact that I am interested in Ubuntu, I am going to dual boot (because my parents do not have much computer xperience). So my question is is how do I, during the installation, still keep windows and install ubuntu, at the same time. How do I make a partition (and what size) during the install of ubuntu. :confused: At the time of the windows installation, we did not make a partition (did not think about switching to linux that much, until i heard of the ease of ubuntu) and that is what is allowing me to switch. Good job Ubuntu. So ya some questions I have. 

On the system I am installing ubuntu:
1) i need video drivers for a nvidia geoforce 2 mx card
     -Where do I get them if I am installing the 32-bit version of Ubuntu. 

On the system of mine that I want to swithch also, but the live cd does not seem to work (Says that my cd drive might be currupt, but that does not make sense to me..cause it does work perfectly in windows....maybe I should check to be sure... ne one else get this error?) 

1) It has a x800xl 512mb video card, where do i get drivers for it... and how. Do I go to the ati site.. heard that is not good, or do I put in a code in the terminal/kernel thingy. 
2) i have a nvidia A8N-E mobo, where do I get drivers for that..the actual nvidia site(which one). 

Thx guys this really helps me out. I am new..well that is obvious, thx for ur help. It is nice to have people to help me out. :mrgreen:[/QUOTE]


See [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm") for a nice walkthrough on installing Ubuntu when you already have Windows.

For most desktop users, Ubuntu comes with reasonable graphics drivers. Just install now and see if you want to install extra drivers. But first, get used to installing applications "Linux way" and find out how things are done. Then you'll have easier time installing drivers and tweaking your computer.

Your troubles with cd may be caused by an error while downloading (did you check md5 sum?), error while burning or it might be an issue with that cd-rom drive. (I once had a broken cd-drive which worked _reaally_ slow with Windows but I couldn't install Ubuntu with it.)

---

### Post by Nitrous570 on 2006-02-06
[QUOTE=lha]See [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm") for a nice walkthrough on installing Ubuntu when you already have Windows.

For most desktop users, Ubuntu comes with reasonable graphics drivers. Just install now and see if you want to install extra drivers. But first, get used to installing applications "Linux way" and find out how things are done. Then you'll have easier time installing drivers and tweaking your computer.

Your troubles with cd may be caused by an error while downloading (did you check md5 sum?), error while burning or it might be an issue with that cd-rom drive. (I once had a broken cd-drive which worked _reaally_ slow with Windows but I couldn't install Ubuntu with it.)[/QUOTE]

I am thinking that it is a problem with my drive, due to the fact that it is working on my cd atm. And yes ty for the link on installing ubuntu with windows.. i hope that it will help (haven't looked through it yet). Thx guys. :D

---

