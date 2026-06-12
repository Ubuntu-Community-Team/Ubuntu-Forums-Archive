---
title: "Stuck at pink screen and other problems"
date: 2011-06-07
forum: General Help
---

### Post by Maarij on 2011-06-07
I've  tried everything I could think  up of so I thought I would ask online.  About 3 days ago my dad got an email and when he opened the attachment,  the computer crashed. After trying to reboot it, it would just hang at a  black screen but you could tell that the computer was loading  something. The computer does in fact load back into W7 but only after ~4  hours. At first we tried booting from disk with a W7 disk but it would  completely skip the boot part and just ask me which OS to use with W7  being the only option because it was the only OS installed on there.  Even after selecting to start W7 in safe mode, the computer would stake  take a couple of hours to get into windows. After this I tried an Ubuntu  boot from disk and installing that but once I got into the selections  menu for Ubuntu, the system would start taking extremely long load times  again. I did not go through with the Ubuntu installation at that time  but instead burned "Darik's Boot and Nuke" and compeletely erased  everything from the hard drive. I then put in the Ubuntu disk again and  tried installing it and everything seemed to be going fine until it  started actually installed. I installed it on a 200GB partition with  12GB of swap. The installation took 4+ hours as I went to bed so do not  know the exact time. After restarting when it finished installing  Ubuntu, it would just start and stay at a pink default screen at the  start and would not load anything beyond that. I tried the W7 boot disk  again after this and again deleted all the partitions and formatted it  again and am currently installing W7 again but am not sure if it will  work. Would anyone have any info on what could be wrong?

---

### Post by airspoon on 2011-06-07
I'm not sure about the Windows 7 or your boot-loader problems, but I did have the same problem with the "pink" screen after installing Ubuntu 11.04. 

From what I have learned about my own problem, which sounds similar to yours (and many other people), is that there is a problem with Ubuntu acknowledging the nvidia driver for particular Nvidia graphics cards.

The work around for me, was to type my username in the field (or click on it), then at the bottom of the screen, choose "Ubuntu Classic."

I'm no expert and in fact, I'm new to Ubuntu myself, but my problem seems to be very similar to yours. Anyway, I hope it helps and good luck.

---

### Post by Toz on 2011-06-07
> **Maarij said:**
> The computer does in fact load back into W7 but only after ~4  hours.> Even after selecting to start W7 in safe mode, the computer would stake  take a couple of hours to get into windows.> The installation took 4+ hours... 
I would hazard to guess that you have issues with your hard drive and/or controller. What happens when you run the LiveCD? Does it load much quicker?

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **airspoon said:**
> I'm not sure about the Windows 7 or your boot-loader problems, but I did have the same problem with the "pink" screen after installing Ubuntu 11.04. 

From what I have learned about my own problem, which sounds similar to yours (and many other people), is that there is a problem with Ubuntu acknowledging the nvidia driver for particular Nvidia graphics cards.

The work around for me, was to type my username in the field (or click on it), then at the bottom of the screen, choose "Ubuntu Classic."

I'm no expert and in fact, I'm new to Ubuntu myself, but my problem seems to be very similar to yours. Anyway, I hope it helps and good luck.

If 11.04 doesn't work, it just means that there might be a bug for your particular hardware at the moment.  Why don't you try 10.10 386 desktop version and see if this works for you..  You can download the ISO from here:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Just use 10.10 32-bit for now, and if you can install from a USB Flash Drive, it will make the installation go that much faster for you too. Here is how you can take the ISO file and put it on a USB Flash Drive:

The instructions for buring it to a USB Flash drive are on number 2:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

If you get stuck or whatever, come on back and let's try figure this out. 

What kind of computer are you running by the way? :)

---

### Post by Maarij on 2011-06-07
I will try running it LiveCD next chance I get and try the other ISO posted as well and see what happens. if I dont come back than that means everything went well :)

---

### Post by linuxinstalledfromhdd on 2011-06-07
That's exactly what you should do at this point, if you want to save yourselves some time. :)  That guide is really clear-cut, and you can't go wrong with that.  :)

---

### Post by Maarij on 2011-06-07
> **Toz said:**
> I would hazard to guess that you have issues with your hard drive and/or controller. What happens when you run the LiveCD? Does it load much quicker?

the computer seems to run fine when i boot from disk and have any cd in there (W7, Ubuntu, Darik's Boot and Nuke) but when it is done with the cd part, it starts going slow again

---

### Post by Toz on 2011-06-07
You could try the Phoronix Test Live CD [http://www.phoronix-test-suite.com/?k=pts_desktop_live]("http://www.phoronix-test-suite.com/?k=pts_desktop_live"), run some drive tests and see what is reported back about the performance.

---

