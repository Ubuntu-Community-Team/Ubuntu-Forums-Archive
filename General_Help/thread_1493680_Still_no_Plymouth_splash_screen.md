---
title: "Still no Plymouth splash screen"
date: 2010-05-26
forum: General Help
---

### Post by todosmentira on 2010-05-26
Hi comrades!

Please disregard the title - this is an issue with the plymouth  splash, not grub.

I have upgraded from Ubuntu 9 to Ubuntu 10.04 and I have an ATI 4850 with propriety drivers installed. I have tried about every fix for this including:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

and the startup manager workaround; I have been careful to set gedit to my monitor's native resolution 1440x900

Every fix has just given me varying degrees of graphical corruption and/or no splash image; I get a nice splash when shutting down. What's going on??? Help appreciated.

---

### Post by _Mark_ on 2010-05-26
Are you talking about Grub or Plymouth?

You're title says grub but the link is about plymouth, if it is about plymouth read the sticky at the top of the general help forum

If none of the fixes worked you may have to live with it, strange thing is mine wasn't working after the initial install but now is and I don't think i did anything to change it

---

### Post by todosmentira on 2010-05-26
sorry  -I do mean plymouth, if this is the splash with the ubuntu logo and the dots. (I'm a bit new to linux) I have followed the workarounds in the sticky.

---

### Post by garvinrick4 on 2010-05-26
If you need splash screen to show up on boot then open a terminal and use this Code.

go to root
```
sudo -s
```fix from Scott James Remnant bug #540801
 ```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
  update-initramfs -u

```out of root


```
Ctrl/D
```
reboot and graphics drivers will start before mounting of partition and you
will have a splash screen. If you want to read about boot up process the packages are
ureadahead, mountall and plymouth.

---

### Post by todosmentira on 2010-05-26
> **garvinrick4 said:**
> If you need splash screen to show up on boot then open a terminal and use this Code.

go to root
```
sudo -s
```fix from Scott James Remnant bug #540801
 ```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
  update-initramfs -u

```out of root


```
Ctrl/D
```reboot and graphics drivers will start before mounting of partition and you
will have a splash screen. If you want to read about boot up process the packages are
ureadahead, mountall and plymouth.

Hi - thank you -followed these instructions but now I simply have a new corruption (screen filled with vertical green lines ) at splash.
Has anyone with my setup (4850 +proprietry driver + 10.04) actually managed to solve this?

---

### Post by todosmentira on 2010-05-26
bumping - still no solution - I would be interested to hear if anyone has a high res working splash with a 4850 Ubuntu 10.04 and ATI drivers?

---

### Post by todosmentira on 2010-05-28
anyone? followed all suggestions on this forum - beginning to think this is a bug with ubuntu and ATI 4850. strange thing is it worked fine with ubuntu 9

---

### Post by garvinrick4 on 2010-05-28
> **todosmentira said:**
> anyone? followed all suggestions on this forum - beginning to think this is a bug with ubuntu and ATI 4850. strange thing is it worked fine with ubuntu 9
If you used startupmanager why don't you try using a lower setting like 800/600 or even the lowest just for the heck of it. Change the OS in the top of your boot screen's startupmanager, the default OS. For some
reason your graphics drivers are not loading before mountall and you get no plymouth, no reason you are mounting already. I do not know what you have startupmanager set at but if it is high then you must have awful small fonts in boot. I am just setting yours like mine just because mine works. Do not have a graphics card such as yours and just a shot in the dark. Cannot hurt anything. Good luck partner.

---

### Post by todosmentira on 2010-05-28
> **garvinrick4 said:**
> If you used startupmanager why don't you try using a lower setting like 800/600 or even the lowest just for the heck of it. Change the OS in the top of your boot screen's startupmanager, the default OS. For some
reason your graphics drivers are not loading before mountall and you get no plymouth, no reason you are mounting already. I do not know what you have startupmanager set at but if it is high then you must have awful small fonts in boot. I am just setting yours like mine just because mine works. Do not have a graphics card such as yours and just a shot in the dark. Cannot hurt anything. Good luck partner.

Hi thanks - tried this on several resolutions including 800x600 and changed OS (don't really understand what this means as the OS is installed anyway) and still just get corruption - vertical lines fill screens in different colours depending on res selected in startup manager.

---

### Post by philinux on 2010-05-28
Main thread title amended.

---

### Post by todosmentira on 2010-06-01
bump - still no working splash - does anyone have any solutions or would be able to look at my configuration (gedit?) please??

---

### Post by dcstar on 2010-06-01
> **todosmentira said:**
> bump - still no working splash - does anyone have any solutions or would be able to look at my configuration (gedit?) please??

I have a very nice Graphical boot loader as well as the Ubuntu splash screen with my ATI video setup using the 10.04 hardware drivers - I use **burg** instead of grub.

---

