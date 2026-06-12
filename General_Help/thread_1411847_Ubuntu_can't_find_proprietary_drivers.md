---
title: "Ubuntu can't find proprietary drivers"
date: 2010-02-20
forum: General Help
---

### Post by lindsay44 on 2010-02-20
I just installed Ubuntu today and when I go to Hardware Drivers it tells me that there are no proprietary drivers on this system and doesn't show any for me to activate. Oddly enough when I was running the live CD of Ubuntu I got a list of a few drivers to activate, namely the Broadcom STA Wireless Driver and the NVIDIA Accelerated Graphics Driver (version 185).  If anyone could give me any help I would really appreciate it. Thanks in advance!

---

### Post by Pjotr123 on 2010-02-20
Hook your machine temporarily on an ethernet cable (wired internet) and retrieve the drivers, by means of System - Administration - Hardware Drivers. Choose Broadcom STA (stable) for your wireless, and not the other Broadcom option.

---

### Post by lindsay44 on 2010-02-20
Thanks for the help, but even when I'm on an ethernet connection, the Hardware Drivers screen is blank with the "no proprietary drivers are in use on this system" message. Is there anything else I can do to get these drivers?

---

### Post by GSF1200S on 2010-02-20
Ive had this issue too in the past. I really dont understand WHY it does this. You can try rebooting, and sometimes that works. However if it doesnt, try:

```
sudo jockey-gtk
```

and with any luck it will popup with your video card and broadcom card. I dont know if its a gksudo bug (graphical apps are supposed to be run with gksudo [or kdesu for kde]), but running sudo in front of jockey-gtk has worked for me ALMOST everytime.

Alternately, you can go to nvidia's website and download their latest driver. Put it in your home folder, and rename it nvidia.run so its easier to work with. Open a terminal and type (DONT DO THIS UNTIL YOU READ THIS POST OR PRINT IT OUT- YOUR DESKTOP WILL GO AWAY):

```
sudo /etc/init.d/gdm stop
```

You will be at a barren command line now (you may need to login, but prolly not). Now, run this command:

```
sudo sh nvidia.run
```

Tell it yes to everything it asks, and then youll be back at the command line. Then put in:

```
sudo nvidia-xconfig
```
and finally:
```
sudo /etc/init.d/gdm restart
```\

Good luck :)

---

### Post by lindsay44 on 2010-02-20
Thanks for the reply! I tried restarting and then ```
sudo jockey-gtk
``` but unfortunately I kept getting the same blank screen. Then when I tried your second solution after typing in ```
sudo sh nvidia.run
``` I got a message saying something like nvidia.run could not be started. Is there anything else I could try?

---

### Post by howefield on 2010-02-20
> **lindsay44 said:**
> I just installed Ubuntu today and when I go to Hardware Drivers it tells me that there are no proprietary drivers on this system and doesn't show any for me to activate.

Have you updated your package list ?

With your ethernet connection connected, open a terminal (Applications > Accessories > Terminal) and type

> sudo apt-get update

Then try Hardware Drivers again.

---

### Post by GSF1200S on 2010-02-20
> **lindsay44 said:**
> Thanks for the reply! I tried restarting and then ```
sudo jockey-gtk
``` but unfortunately I kept getting the same blank screen. Then when I tried your second solution after typing in ```
sudo sh nvidia.run
``` I got a message saying something like nvidia.run could not be started. Is there anything else I could try?

I really need to know that exact error message- I might be able to help you there. 

I guess you can try installing the nvidia driver from the command line, and then do nvidia xconfig. It would go like this:
```
sudo /etc/init.d/gdm stop
```
```
sudo apt-get update
```
```
sudo apt-get install nvidia-glx-185
```
```
sudo nvidia-xconfig
```
```
sudo /etc/init.d/gdm restart
```

Can you get that error message posted up here so others might be able to help you if Im not able to? Then try the above commands and see what happens.:)

---

### Post by GSF1200S on 2010-02-20
> **howefield said:**
> Have you updated your package list ?

With your ethernet connection connected, open a terminal (Applications > Accessories > Terminal) and type



Then try Hardware Drivers again.

If this fixes his/her problem, im going to be happy for him/her and angry at you ;)

---

### Post by northd_tech on 2010-02-20
Have you tried downloading the STA driver directly from Broadcom? See post #2 here:

[http://ubuntuforums.org/showpost.php?p=8848805&postcount=2](http://ubuntuforums.org/showpost.php?p=8848805&postcount=2)

---

### Post by northd_tech on 2010-02-20
> **Pjotr123 said:**
> Hook your machine temporarily on an ethernet cable (wired internet) and retrieve the drivers, by means of System - Administration - Hardware Drivers. Choose Broadcom STA (stable) for your wireless, and not the other Broadcom option.

The "other" Broadcom driver would be "b43" and its associated "ssb" module.  There are older threads here about that, and it involves "fwcutter" to get the Broadcom firmware, and blacklisting modules, and ...

I'd just stick with the Broadcom STA driver if you can get it to work.  

I have read where people needed to unplug the ethernet cable and restart in order to get the STA driver to activate.  1 or 2 people also had to Remove then re-Activate the STA driver and restart ubuntu to get the wireless working.

---

### Post by lindsay44 on 2010-02-20
:D Thanks to everyone who replied! It was                               "sudo apt-get update" that solved my problem. I've updated the thread to say solved. Thanks again to everyone!

---

### Post by GSF1200S on 2010-02-20
> **lindsay44 said:**
> :D Thanks to everyone who replied! It was                               "sudo apt-get update" that solved my problem. I've updated the thread to say solved. Thanks again to everyone!

Thanks for updating the thread.. Glad it got fixed :)

---

### Post by howefield on 2010-02-20
> **GSF1200S said:**
> If this fixes his/her problem, im going to be happy for him/her and angry at you ;)

Actually, I was thinking something similar ;)

Easier to start with the simple stuff and work your way up to the tougher options.

Sorry to make you angry...

---

### Post by GSF1200S on 2010-02-20
> **howefield said:**
> Actually, I was thinking something similar ;)

Easier to start with the simple stuff and work your way up to the tougher options.

Sorry to make you angry...

Yeah, for sure.. Coming back from Arch, im not used to simple stuff, haha... Im not angry, as you know ;)

---

### Post by howefield on 2010-02-20
> **GSF1200S said:**
> Yeah, for sure.. Coming back from Arch, im not used to simple stuff,

That's odd, given that Arch "tries to Keep It Simple".

> haha... Im not angry, as you know ;)

I know :)

@lindsay44, glad you're sorted.

---

### Post by northd_tech on 2010-02-22
I just read earlier today where removing the linux kernel backports (and sources?) got one person's proprietary "Hardware Drivers" to come back from NeverNeverLand- that might be worth a shot (especially if you have spare kernels to experiment with).

---

