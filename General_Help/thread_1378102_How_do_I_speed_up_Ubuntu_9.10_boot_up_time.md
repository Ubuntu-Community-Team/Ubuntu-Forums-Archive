---
title: "How do I speed up Ubuntu 9.10 boot up time"
date: 2010-01-11
forum: General Help
---

### Post by Vignesh S on 2010-01-11
Despite the fact that Ubuntu 9.10 boots up faster than its predecessors (I didn't time the boot up myself, so I can't say for sure), my Ubuntu laptop still takes around 50 seconds to boot up fully. Now I'm not happy with that, and I want it to boot up even *faster*. 

Any suggestions as to how I could do this?

---

### Post by Vignesh S on 2010-01-11
<bump> surely there is a way to speed up Ubuntu 9.10's boot up time...

---

### Post by zenxi on 2010-01-11
> **Vignesh S said:**
> <bump> surely there is a way to speed up Ubuntu 9.10's boot up time...

try using bum to disable unnecessary stuff 
```
sudo apt-get install bum
```

you could also use preload, a program that learns your most used programs and caches them on login

```
sudo apt-get install preload
```

ailurus is a program used to tweak all aspects of ubuntu 
```
sudo add-apt-repository ppa:ailurus/ppa && sudo apt-get update && sudo apt-get install ailurus
```

---

### Post by warfacegod on 2010-01-11
Here's some simple things:

Turn off as many start up apps as possible (fairly obvious now that I think about it)

Make sure Compiz is off before shutting (my laptop boots about 20 seconds faster with it off)

Don't turn on any externals until you need them

Have as few items on your panels as possible

There's probably hundreds more but my brain stopped working about six hours ago. Try poking around in the Configuration Editor.

---

### Post by zenxi on 2010-01-11
> **Vignesh S said:**
> Despite the fact that Ubuntu 9.10 boots up faster than its predecessors (I didn't time the boot up myself, so I can't say for sure), my Ubuntu laptop still takes around 50 seconds to boot up fully. Now I'm not happy with that, and I want it to boot up even *faster*. 

Any suggestions as to how I could do this?

i forgot to mention before but there is also a lot of different things you can do to firefox to make it faster, and theres a huge thread dedicated to it here [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Macinbomzh on 2010-01-11
Disabling the usplash and gdm would also help, booting like 10 seconds faster for me

---

### Post by Vignesh S on 2010-01-11
> **warfacegod said:**
> 
Make sure Compiz is off before shutting (my laptop boots about 20 seconds faster with it off)


How would I make sure Compiz is off before I shut it down? And how would I disable usplash? 
If I disable GDM, wouldn't that like make it impossible to login graphically?

---

### Post by FreezWay on 2010-01-11
do at your own risk, if u have dual or more cores, #5 helps a lot:

[http://tuxtraining.com/2008/09/28/how-to-make-ubuntu-extremely-fast/](http://tuxtraining.com/2008/09/28/how-to-make-ubuntu-extremely-fast/)

---

### Post by warfacegod on 2010-01-11
> **Vignesh S said:**
> How would I make sure Compiz is off before I shut it down? And how would I disable usplash? 
If I disable GDM, wouldn't that like make it impossible to login graphically?

The easiest way to turn Compiz on and off is CompizSwitch. Search the net for this: compiz-switch_0.4.3~ubuntu-1_all

Don't disable gdm to disable the splash, you may end up having to startx from command line therefor increasing boot time. Macinbomzh can give you better idea about what disabling gdm will do, it seems to work for him.

Read this and the links in it for a better idea of dealing with splash screens:

[http://ubuntuforums.org/showthread.php?t=1376420]("http://ubuntuforums.org/showthread.php?t=1376420")

---

### Post by colsandurz on 2010-01-11
If you dual boot (or maybe if you have multiple kernels that you choose) grub will wait 10 seconds by default.  

You can change this, although I don't think you have this problem.  

Just in case though, if you want to change this delay do this:

```
sudo nano /boot/grub/grub.cfg
```

and change timeout from 10 to whatever you want.  There's a GUI way to do this too, but I forget how, you may be able to do it with bum.

---

### Post by warfacegod on 2010-01-12
Ubuntu Tweak is another app that might help. It's similar to ailurus, the app zexni suggested. It's got some cleaning features like removing older kernels. That should get grub to load faster.

---

### Post by hhh on 2010-01-12
> **colsandurz said:**
> If you dual boot (or maybe if you have multiple kernels that you choose) grub will wait 10 seconds by default.  

You can change this, although I don't think you have this problem.  

Just in case though, if you want to change this delay do this:

```
sudo nano /boot/grub/grub.cfg
```

and change timeout from 10 to whatever you want.  There's a GUI way to do this too, but I forget how, you may be able to do it with bum.

[COLOR="Red"]**DO NOT DO THIS!!! grub.cfg IS NOT TO BE EDITED!!!**[/COLOR]

The proper file to edit is /etc/default/grub

See the Grub2 documentation...
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Vignesh S on 2010-01-12
> **hhh said:**
> [COLOR="Red"]**DO NOT DO THIS!!! grub.cfg IS NOT TO BE EDITED!!!**[/COLOR]

The proper file to edit is /etc/default/grub

See the Grub2 documentation...
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Don't worry, I knew that grub.cfg is not meant to be edited :-P Thanks for the heads up though :-D

---

### Post by Vignesh S on 2010-01-12
> **colsandurz said:**
> If you dual boot (or maybe if you have multiple kernels that you choose) grub will wait 10 seconds by default.  

You can change this, although I don't think you have this problem.  

Just in case though, if you want to change this delay do this:

```
sudo nano /boot/grub/grub.cfg
```

and change timeout from 10 to whatever you want.  There's a GUI way to do this too, but I forget how, you may be able to do it with bum.

Alright, lets sort this out:
1. I just press enter when the GRUB comes up (I dual boot with Win 7) if I want to boot into Ubuntu
2. I said speeding up *Karmic Koala*, not Jaunty or lesser :-P
3. The GUI won't quite work since I don't think that has quite been made for GRUB2 (well, technically GRUB 1.97beta4, but still... :-P)

---

### Post by Macinbomzh on 2010-01-12
Removing the mount within grub of windows hardisk (if you have windows) or any unnecessary hardisks will have a significant effect.
you can mount them later if you wish, it will, basically have the same time to load, but the graphical components will be loaded faster
and the mount won't be included within the 'load' procedure and will give a warm feeling.
you should give windows load manager pop first, and from grub->gdm the procedure will be faster, but this is already on how the
'boot' is defined in your eyes.

Another very common method is just leave it as it is, ubuntu does not necessarily have to load faster than it already does.

If you want any council on how to make the boot faster, you should be more specific on what are your current boot properties.

---

