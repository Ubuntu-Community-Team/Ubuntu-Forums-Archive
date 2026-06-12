---
title: "Showing GUI/Desktop after console."
date: 2011-06-12
forum: General Help
---

### Post by indianabones on 2011-06-12
New to ubuntu, but need it for Uni, would like some help please. I promise you I have searched and looked and tried many of the options, but they all give nothing, or produce errors.
 
I installed Ubuntu 10.10 (CUDA recommendation) and it all went very very well, installed, programs run, resolutions changed and simple programs like hellow world in C and Java work. 
 
Decided to do something following a tutorial from Nvidia which asked for a me to do something in a console, that's tty5 and using **_CTRL + ALT + F5_**. In the end was a pointless thing and send me in the wrong direction.
 
From this console (full screen black and white terminal which has the normal home directory) I've tried **_CTRL + ALT + F7_** to get back to the normal GUI/desktop with you know my files and folders etc, but no luck. It keeps stopping at **_"Checking Battery State..."._**

All I want is, when I start ubuntu, for it to show the desktop instead of the tty5 (**_CTRL + ALT + F5)_** concole or whatever it is.
 
Any ideas?
 
FYI: Ubuntu 10.10 64 Bit.

---

### Post by Penguin Guy on 2011-06-12
What exactly was the tutorial? It might be easier to help you if we know what caused the problem in the first place.

---

### Post by indianabones on 2011-06-12
> **Penguin Guy said:**
> What exactly was the tutorial? It might be easier to help you if we know what caused the problem in the first place.
 
 
Hi,
 
I can't find the original thread it's bookmarked on Ubuntu  in Firefox, which I can't obviously access the at the moment. But here is a similar tutorial, with the same set of instructions.
 
[http://ubuntuforums.org/showthread.php?t=1625433](http://ubuntuforums.org/showthread.php?t=1625433)
 
It's the following steps that caused the problem.
 
[LIST=1]
[*]Reboot your PC.
[*]Go to a virtual terminal (we will need to shut down the X server):
Code:
CTRL+ALT+F5
Some users have reported problems changing between virtual terminals in Ubuntu 10.04. If you have this problem, see the following solution [[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=1473045[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1473045").
[/LIST][LIST=1]
[*]Login at the terminal and run:
[*]Code:
[/LIST][LIST=1]
[*]sudo service gdm stop
[/LIST]
 
 
Now I've read here the solution could be to restart or start GDM, others say CTROL + ALT + F7.
 
When I try the GDM restart/start/stop in tty5, nothing happens. When I try CTRL + ALT + F7, it just says Checking Battery State.... and remains there.
 
I just want to be able to get back to desktop.

---

### Post by nothingspecial on 2011-06-12
First, are you still in this situation? Have you tried rebooting.

To do that from tty5

```
sudo reboot
```

Also, try Ctrl-Alt-F8

If it is not as simple as this, please post a link to the instructions you followed so someone can try to undo them.

Hi, by the way :D

---

### Post by nothingspecial on 2011-06-12
You might want to try
```

sudo service gdm start
```

---

### Post by indianabones on 2011-06-12
Hi, well I've just tried both on Ubuntu again and still the same. I'm typing this from my laptop.
 
1. When the system boots, it goes straight to tty5. If I type the command sudo service gdm start, it says service in start/running process 1678.
 
2. When I type ctrl + alt + f7, it produces some messages but then stops at checking battery state...
 
I did 3 things prior to getting into this pickle, uninstalling my GPU driver, going to tty5 like in the tutorial I've stated above and then the sudo gdm command.

---

### Post by indianabones on 2011-06-13
If anyone ever does search this thread up in the future. Then I found the solution.

If you end up stuck in one of the consoles that's tty1 - tty6, and Ctrl + ALT + F7 doesn't take you to the desktop.

Simple try the following command.

[CENTER][LEFT]
[LIST]
[*]**sudo apt-get install nvidia-current**
[/LIST]

RUn through everything by pressing enter, it will take care of all the older versions of drivers for you as well. Nvidia update their drivers regularly and I guess that's where the problem was.

This followed by:


[LIST]
[*]**sudo nvidia-xconfig**
[/LIST]
did the job for me, in fact, I reckon, just the install of the driver was enough for me. 


[/LEFT]
[/CENTER]

---

