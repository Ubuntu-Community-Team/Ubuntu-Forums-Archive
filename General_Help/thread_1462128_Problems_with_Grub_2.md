---
title: "Problems with Grub 2"
date: 2010-04-25
forum: General Help
---

### Post by oxf on 2010-04-25
Hi,
 
I'm having a few issues with Grub 2 in Karmic. Before getting into them two basic questions:
 
If I re-install Grub 2 from the live CD should that reset all the personalisations such as as splash screen colours in the Grub splash to default? In my case they are not resetting. I would have expected them to revert to the default black/white you get when initially installing the OS. So I'm wondering if it's being fully reinstalled? although it tell me so when I do it. 
 
Also has anyone else experienced the Grub countdown timer to be a lot less than its supposed to be? e.g. the default timeout setting is 5 seconds but in reality its more like 2 or 3 seconds  and when I set my prefered timeout value to 2 seconds it results in being about 1/4 sec or so! just a very quick flash in fact.

Thanks

---

### Post by warfacegod on 2010-04-25
GRUB uses a file in your OS for its settings (don't remember where it is). This aught to help:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics")

---

### Post by oxf on 2010-04-25
> **warfacegod said:**
> GRUB uses a file in your OS for its settings (don't remember where it is). This aught to help:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics)

Yes thanks, I was aware of that.

The settings are stored in ***/etc/grub.d/05_debian_theme***.
Maybe its not changed when grub is reinstalled?

But the countdown timer thing is really weird

---

### Post by warfacegod on 2010-04-25
If you are simply reinstalling GRUB then no, I don't think the file will be reinstalled. It should stay the way it is.

As for that time thing, it sounds to me like the System Time in your BIOS is fragged. Have you changed the CMOS battery?

---

### Post by oxf on 2010-04-25
> **warfacegod said:**
> If you are simply reinstalling GRUB then no, I don't think the file will be reinstalled. It should stay the way it is.

As for that time thing, it sounds to me like the System Time in your BIOS is fragged. Have you changed the CMOS battery?

Hmm maybe? I havent changed it but I dont think thats the problem. Everything was fine until yesterday, i.e "Coundown Timer =5" resulted in five secs, "=2" two secs and so on.

Then I started messing with the splash colors as instructed in 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 
and the Countdown Timers no longer reflects the setting so I think it was something I did. I would have thought a Grub reinstall would have fixed it but nooo! :confused:

---

### Post by warfacegod on 2010-04-25
I'd say use your LiveCD to get a copy of the default GRUB file and replace the one in your OS with it. If you do, it might be wise to ```
sudo update-grub
``` afterwards.

---

