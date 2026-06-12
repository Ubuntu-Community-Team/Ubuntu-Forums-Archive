---
title: "Ubuntu keeps crashing !"
date: 2010-08-01
forum: General Help
---

### Post by Pizzamus on 2010-08-01
Hi  everyone, 
I hope I post in the correct forum.

I installed ubuntu on my laptop a few weeks ago and it keeps crashing nearly eveerytime i use it.

It usually works fine when it boots, then i go on firefox, do some stuff, do some programming, and generally after 20 or 30 minutes it crashes, here are the symptoms :

*[COLOR=Red]**the keyboard stops working. if I click on any of the icons on the top bar "Application, Places, System, Shutdown " etc it doesnt do anything at all.**[/COLOR]*

**The only way is to shut down by pressing the power button**

I run a dual boot with windows 7, also a fresh install ( same date as ubuntu).

I dont know if you need more information... my laptop is an HP pavillion , processor is AMD TURION dual core 1.9ghz, 2gigs ram, nvidia graphic card ...

Also sometimes, when my ubuntu boots, the sound card is not recognized ( that happened twice )

If you need more info on my ubuntu version etc, please tell me how to do as im quite new to this 
Thanks a lot in advance :)

---

### Post by Pizzamus on 2010-08-01
so can no one help ?

---

### Post by dreamsR4living on 2010-08-01
Does the system freeze totally, I mean are you not able to even move your mouse anymore? Well sometimes it does work but mostly it hangs?

This is an issue that has been around in Ubuntu for a long time, see this post from 2008 with 51 pages; [http://ubuntuforums.org/showthread.php?t=765510](http://ubuntuforums.org/showthread.php?t=765510).

Maybe you can find some info there. If your system freezes totally look around at the forum for (I presume that you use lucid, 10.04) "Lucid Freezes" I am sure you will find some information.

There is still not one solution as the freezes have many different causes, such as hardware or Ubuntu bugs that make some computers, specially laptops to freeze. In my case I have been experiencing freezes in 8.04 and 8.10, but all versions before and after were freeze free on my machine.

Try to find more information what causes the freezes on your computer. I don't know if you used another Ubuntu version before that just worked? If so, reinstall that version until a new Ubuntu comes out (even better, keeps it as it totally works). Or try another Ubuntu or Debian based Linux distro, such as [Linux Mint]("http://linuxmint.com/"). 

Or, when you are ready to use older, but rock-solid software use [Debian 5]("http://www.debian.org/") (lenny). Debian is a lot more difficult to configure specially when you are new to Linux, for it is a specialized Linux distro, but once you got it working you will almost find no bugs or crashes.

---

### Post by Pizzamus on 2010-08-06
Well i can still move the mouse around but cliking has no real effect. I can usually close the applications which are open, but I cannot open anything or use any button of the upper taskbar, including the one to shutdown. 

I guess it might be because I have an HP laptop and they tend to be a bit crap !!


My friend installed that version for me a few weeks ago so I haven't used any other.

Also, I said I was using a dual boot with windows 7, so when I boot my laptop, I get a choice between my different OS.
Before I had just the choice of Linux 2.6.32.23, Windows 7 and a memory test ( I dont know why )

However, I installed updates and now i also have the choice to start on Linux 2.6.32.24 when i boot my laptop.

I would like to remove the older version from the boot screen but I dont know how to do that.

I went to my /boot directory and there's a number of similar files except some are for 2.6.32.23 and the other for 2.6.32.24

Is it safe to remove the old ones and keep the new ones only ? 
I wouldnt want to mess up my boot and no longer be able to use my laptop :p

Btw I don/t know if its the standard boot manager, but my friend installed Grub.

---

### Post by mike555 on 2010-08-06
kinda sounds like a heat issue , is it over heating ? have you tried putting it on a cooling pad?

---

### Post by Pizzamus on 2010-08-06
Well yeh my laptop always had overheating issues bu now with 7 and linux they are gone. Also I cleaned the vents which improved it quite a lot.

---

### Post by dreamsR4living on 2010-08-06
I cannot help you any further with your laptops freezing issue...

> Also, I said I was using a dual boot with windows 7, so when I boot my laptop, I get a choice between my different OS.
Before I had just the choice of Linux 2.6.32.23, Windows 7 and a memory test ( I dont know why )

However, I installed updates and now i also have the choice to start on Linux 2.6.32.24 when i boot my laptop.

I would like to remove the older version from the boot screen but I dont know how to do that.

I went to my /boot directory and there's a number of similar files except some are for 2.6.32.23 and the other for 2.6.32.24

Is it safe to remove the old ones and keep the new ones only ?
I wouldnt want to mess up my boot and no longer be able to use my laptop

Btw I don/t know if its the standard boot manager, but my friend installed Grub.

Do you know if your friend installed GRUB 1 or GRUB 2 1.98? If you don't know you can check it by going to the System >> Administration >> Synaptic Package Manager and type grub to see which GRUB you are using.

If you have GRUB 1 I have good news for you, because it gives you a lot of control about what to display in the boot menu. If you have GRUB2 1.98 you have a problem, because the new GRUB is everything but configurable. Well you don't have such a big problem, but in this case I don't have a clue how to delete the old kernels from the grub menu.

It is not dangerous to delete the old kernels from the GRUB menu at all.

Read this if you want to delete your old kernels totally from your system; [http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/). It will also delete the old kernels from GRUB. **BUT BE CAREFUL NOT TO DELETE YOUR CURRENT KERNEL!!**

If I were you I should first look what GRUB you are using, because it would make no sense to remove old kernels and potentially harm your system, just for the sake of cleaning up your GRUB menu.

---

### Post by Pizzamus on 2010-08-07
Hi,
I checked and I'm using the 1.98-lubuntu7 version 2 ...
and yes I had a look at the config menu the other day and the only thing i could configure was the default OS and loading time ... thats already a good starting point but there's nothing else useful... 

I'll have a look at that article, in the mean time i'll back up my system just in case :) 
The only problem is my friend lives in a different country so i'd rather wait for him to come in a few months rather than risk destroying my laptop lol 

thanks for the help so far

---

### Post by Pizzamus on 2010-08-07
Well that article was easy enough to understand, I did it and it worked perfectly well ! 
thanks a lot

---

### Post by dreamsR4living on 2010-08-08
> Well that article was easy enough to understand, I did it and it worked perfectly well !
thanks a lot

Great that it worked for you! :D

---

