---
title: "No fan control w/9.10?"
date: 2009-11-05
forum: General Help
---

### Post by sir biscuit on 2009-11-05
Just recently upgraded to 9.10 on desktop-all my case & cpu fans @100%!! Sounds like a jet now,run pwmconfig...says I fave no pwm fans?? I have 3,9.04 saw them. I could use some help taming the beast! I am a newbie to linux,so be gentle!:lolflag:

---

### Post by sir biscuit on 2009-11-05
I forgot to add,I tried to install may fan program that works on my xp side w/wine-driver won't install..:confused:

---

### Post by ^_Pepe_^ on 2009-11-05
Hi!

Don't worry, you're not alone! There is a bug (or a driver change that is not working propoerly) here. 

1st. What motherboard do you have?
2nd. If you run sensors-detect.. is there any driver detected?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246)
[https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/336418](https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/336418)

Are cases. It depends on if your motherboard is going to respond to the new driver. If not, you need to blacklist the new drivers, and if yes, you need to upgrade to lm-sensors 3.1.1

Hope it helps.

Regards,
^_Pepe_^

---

### Post by ^_Pepe_^ on 2009-11-05
More information here,

[http://ubuntuforums.org/showthread.php?t=871001](http://ubuntuforums.org/showthread.php?t=871001)
[http://ubuntuforums.org/showthread.php?t=1211315](http://ubuntuforums.org/showthread.php?t=1211315)

The best,
^_Pepe_^

---

### Post by sir biscuit on 2009-11-05
Will try out tonite,I see others having same issuse since posting last night!):P

---

### Post by sir biscuit on 2009-11-06
My mobo is a Aopen brand w/ fan control. It was seen in 9.04(had monitors ontop in taskbar),but when 9.10 installed,thoses left. I still have cpu,gpu&hdd. Might have to wait till next update,don't have a clue how to compile on my on:confused:.

---

### Post by ^_Pepe_^ on 2009-11-06
Hi!

I'd recommend to go by the easy way.

Edit your /boot/grub/menu.lst, look for "[FONT="Lucida Console"]kopt=root[/FONT]" line, and without removing # character, add, [FONT="Lucida Console"]acpi_enforce_resources=lax[/FONT].

Type

```
sudo update-grub
```


As told here [http://ubuntuforums.org/showpost.php?p=8142711&postcount=15](http://ubuntuforums.org/showpost.php?p=8142711&postcount=15)

Restart and tell us if it works.

Regards,
^_Pepe_^

---

### Post by sir biscuit on 2009-11-07
Will try as soon as I can figure out how to edit grub-newbie to linux!:rolleyes:

---

### Post by ^_Pepe_^ on 2009-11-09
Hi again,

Just:

```
sudo gedit /boot/grub/menu.lst
```

And now, be very careful.

Look for this line

```
# kopt=root=UUID=xXXXXxxxXXXXX ro
```

Obviously, XXX are numbers. 

And add

```
# kopt=root=UUID=xxXXX ro acpi_enforce_resources=lax
```

Hope it helps!

Regards,
^_Pepe_^

---

