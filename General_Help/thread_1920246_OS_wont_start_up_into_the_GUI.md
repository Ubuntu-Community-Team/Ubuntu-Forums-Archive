---
title: "OS wont start up into the GUI"
date: 2012-02-04
forum: General Help
---

### Post by sid.mallya on 2012-02-04
Hey guys!

I have Ubuntu 11.10 installed on one of my laptop's partitions. It was working just fine until a few hours ago. I restarted the computer because I had some work on the windows partition and haven't been able to log into Ubuntu since.

I have tried sudo stop (then start) gdm .. but that isn't working - cause apparently I am signed in already.

sudo start lightdm brings me back to the console (where the last kernel message is "starting CUPS" .. 

What could be wrong? :confused:

---

### Post by raja.genupula on 2012-02-04
type **startx** at console , is it taking to GUI  ? 

and try this also
```
sudo stop gdm
```
```
sudo start lightdm
```

all the best man.

---

### Post by sid.mallya on 2012-02-04
Hey thanks for the quick reply Raja .. I had already tried doing that. 

It seems lightdm is crashing. The last message that I see on the console (before lightdm should ideally start up) is "starting CUPS printing" something :P

Is there a way I could re-install lightdm? Also, I dont have to stop GDM because the instance hasn't been started at all .. :confused:

---

### Post by sid.mallya on 2012-02-04
Bump! Need help guys .. I have some important stuff on the ext4 partition which I cant access thru Windows. :(

---

### Post by Rodney9 on 2012-02-04
Sorry I don't know how to fix your problem, however you should be able to get to your files with a live CD/DVD, most likely the one you installed with.

Rodney

---

### Post by sid.mallya on 2012-02-04
Hehe .. Yea. Already did it .. Thanks!

But I still need to fix the problem. Could there be any space issues? I think the disk space for ext4 was running low .. =S

---

### Post by jerrrys on 2012-02-04
Yes, that could indeed be it.

In terminal enter:  df

Are you full up?

sudo apt-get clean

That may buy you some room.

---

### Post by raja.genupula on 2012-02-04
I have got some information for you that's really helpful to you.

open this link :[https://wiki.ubuntu.com/LightDM/](https://wiki.ubuntu.com/LightDM/)

and type **ctrl+F** and paste **What to do if things go wrong** in the search box . 

Thats gonna solve your issue . 

Hope that helps.

All the best and let us know what you got .

---

### Post by sid.mallya on 2012-02-05
@Jerrys

U r right! My df in / partition showed 100% .. so I ran a apt-get clean command to free up some space. Now lightdm is working fine.

How do I free up more space in / ? Is there a way I can remove the earlier Linux kernels, etc?

---

### Post by raja.genupula on 2012-02-05
> **sid.mallya said:**
> @Jerrys

U r right! My df in / partition showed 100% .. so I ran a apt-get clean command to free up some space. Now lightdm is working fine.

How do I free up more space in / ? Is there a way I can remove the earlier Linux kernels, etc?

```
sudo apt-get autoremove
sudo apt-get autoclen
```

EDIT :one more useful one 
[http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/](http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/)

---

### Post by sid.mallya on 2012-02-05
Did autoclean and autoremove! Haha .. Google to the rescue .. :D

Btw .. now the synaptic package manager is acting crazy. Wont start up at all .. =S

It asks for the root password then just doesnt show up .. I did a get-update && get-upgrade - which is working just fine.

---

### Post by raja.genupula on 2012-02-05
try to launch it from terminal. If its not shown up then paste the output of terminal here .

---

### Post by jerrrys on 2012-02-05
When you updated you used up the little space you had.

You need to resize your partition.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Gparted is on the Ubuntu Live CD, no need to download it.

Hi raja

---

### Post by sid.mallya on 2012-02-06
Hi! 

I am sorry, can someone tell me how to launch Synaptic Package manager from the terminal? I know how to launch aptitude .. but that's different, isn't it?

Also, because the manager isn't starting up, my update manager has also gone crazy. WTF is happening?

---

### Post by sid.mallya on 2012-02-06
@jerrys

Oh, I cant resize my partition now. Its complicated .. lol .. anyway, I am thinking of removing the earlier kernels of Linux. I think that would create sufficient space .. =/

---

### Post by raja.genupula on 2012-02-07
look at post #10 i have given a link ,scroll down , that will help you removing kernels from terminal .

hope that helps.

---

