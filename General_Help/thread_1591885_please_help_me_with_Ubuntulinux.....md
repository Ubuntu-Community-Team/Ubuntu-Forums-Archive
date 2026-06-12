---
title: "please help me with Ubuntu/linux...."
date: 2010-10-10
forum: General Help
---

### Post by freakyguy88 on 2010-10-10
i need help! i dont know how to run a .RUN file in ubuntu, gnome environment

---

### Post by xnostradamusx on 2010-10-10
[http://ubuntuforums.org/showthread.php?t=239797](http://ubuntuforums.org/showthread.php?t=239797)

---

### Post by freakyguy88 on 2010-10-10
i dont understand any of this!!! is there a program that will do it for me??

---

### Post by xjesse on 2010-10-10
What exactly are you trying to install?

---

### Post by freakyguy88 on 2010-10-10
nvidia drivers in the .run format

---

### Post by xjesse on 2010-10-10
Try going to System > Administration > Hardware Drivers. Does your card show? If so, you'll be able to install the drivers from there.

I'm sorry to say but the link above is very detailed and teaches exactly how to install a .bin. 

Just make sure what you're trying to install isn't in the repositories. If it is, things would be much easier. :)

---

### Post by freakyguy88 on 2010-10-10
> **xjesse said:**
> Try going to System > Administration > Hardware Drivers. Does your card show? If so, you'll be able to install the drivers from there.

I'm sorry to say but the link above is very detailed and teaches exactly how to install a .bin. 

Just make sure what you're trying to install isn't in the repositories. If it is, things would be much easier. :)

no it doesnt show my card, does that mean its not compatible??

---

### Post by xjesse on 2010-10-10
> **freakyguy88 said:**
> no it doesnt show my card, does that mean its not compatible??

No, it just means it's not proprietary. 

Let's see if I can somehow simplify how to install a .run.

Open a terminal. 
Where did the .run download to? Was it your desktop? Was it your Downloads folder? My downloads always go to my Downloads folder.

So in a terminal I would type: 

```
cd Downloads
```

to move into the needed directory.

Next, we set up permissions by typing:

```
sudo chmod +x **FILENAME**.run
```

Finally we will execute it by typing:

```
sudo ./**FILENAME**.run
```

Obviously **FILENAME** needs to be the name of YOUR .run. I hope this helps.

---

### Post by 3rdalbum on 2010-10-10
Do not install the NVIDIA driver manually unless you have a very new card that is only supported by the latest driver.

Get an internet connection, go to Synaptic Package Manager and click Reload. When done, close Synaptic and go to Hardware Drivers to do the automatic installation.

---

### Post by freakyguy88 on 2010-10-10
guys, im going to try freebsd as ive heard its easier. i deleted my ubuntu VM/OS so theres no point in replying to this anymore, thanks for trying (:

---

### Post by xjesse on 2010-10-10
Have fun with the installer. :lolflag:

---

