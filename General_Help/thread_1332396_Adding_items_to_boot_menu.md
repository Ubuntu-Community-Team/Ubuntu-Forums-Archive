---
title: "Adding items to boot menu"
date: 2009-11-20
forum: General Help
---

### Post by Deborah Armstrong on 2009-11-20
I run a karmic server with some additional applications installed. For simplicity in this explanation, there's one resource-hungry task I will call "big". 

Most of the time when I boot, I do want big to run. But occasionally, I want to boot without invoking big.

So I have two related issues. First, I need to learn how to add an entry to the boot menu,  and make sure it is not the default. If there's no user interaction, the system will boot and automatically run big.

Second, I need to figure out how to pass a variable from the boot process to the running  linux to tell it whether big should be invoked.

I am comfortable with the command line, and writing little scripts. But I am not comfortable  with the way much of what I've learned the past eight years keeps becoming depricated. It also seems that as the complexity of linux increases, the quality and accessibility of up-to-date documentation declines. 

Is there a clear tutorial on how this new-fangled grub should be configured? It looks like you no longer modify menu.lst, or grub.cfg or whatever it's called these days. What file then *DO* you edit to add an entry?

Also, how do you pass a variable from grub to the running linux? Pointers to a tutorial about that would also be great.

Lastly, do I use rc.local to invoke big, and where do I add the if statement and the lines  of code to run big? On an old debian system, rc.local was quite straightforward, but on this new karmic release, it's confusingly convoluted.

Help is most definitely appreciated. 

--Debee

---

### Post by diesch on 2009-11-20
> **Deborah Armstrong said:**
> 
Is there a clear tutorial on how this new-fangled grub should be configured? It looks like you no longer modify menu.lst, or grub.cfg or whatever it's called these days. What file then *DO* you edit to add an entry?


See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Basically you add your entries in /etc/grub.d/40_custom


> **Deborah Armstrong said:**
> 
Also, how do you pass a variable from grub to the running linux? Pointers to a tutorial about that would also be great.

*/proc/cmdline* contains the *linux* line from your Grub menuentry. Add some parameter there (make sure it's not one already used) and check if it's there in your in your boot script (e.g. using grep).

> **Deborah Armstrong said:**
> 
Lastly, do I use rc.local to invoke big, and where do I add the if statement and the lines  of code to run big? On an old debian system, rc.local was quite straightforward, but on this new karmic release, it's confusingly convoluted.


/etc/rc.local is empty except for some comments in my karmic.

You may want to write your own init script (use /etc/init.d/
skeleton) to be able to easily start/stop big.

---

### Post by bodhi.zazen on 2009-11-20
Depends on your boot script, but IMO easiest is to use runlevels.

If you want big to run by default, set it to run on runlevel 2 , and if you do not want big running, boot to run level 3, simply by adding a 3 to the end of the kernel line.

The exact details depend on your init script .

---

### Post by Deborah Armstrong on 2009-11-21
>The exact details depend on your init script .
Okay, I understand runlevels but not how init scripts work exactly in Ubuntu. I searched the official docs and can't find a clear explanation about how they work and how to add/modify items. It looks like there are tons and tons of little numbered scripts. 
I don't have a problem reading manuals, but so much out there is depricated. Can I trust info for example from the"Debian Reference" when I'm working on Ubuntu?
Thanks also to the poster who told me about  the file to edit to add an item to the grub  menu, the community documentation still has you editing menu.lst.

---

### Post by Deborah Armstrong on 2009-11-21
Thanks, exactly the info I needed!

---

### Post by bodhi.zazen on 2009-11-22
glad it is working for you. 

In terms of boot scripts, yes they are all changing now, and many distros are moving to Upstart.

The old script and sysvinit scripts work, because we are in transition, so init scripts are moving to Upstart, but not everything has been converted.

sysvinit scripts go in /etc/init.d and you link them to /etc/rcx.d (where X = your run level) and / or use update-rc.d ...

upstart scripts go in /etc/init and you specify which runlevels run the script within the script.

---

