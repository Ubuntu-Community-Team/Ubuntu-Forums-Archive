---
title: "Ubuntu Won't Boot (Low Graphics Mode?)"
date: 2011-01-07
forum: General Help
---

### Post by zacharyh on 2011-01-07
I was uninstalling some programs that I installed to try and get my iPod touch working with Ubuntu (I gave up on that :P) when ubuntu just crashed. Now after I choose ubuntu in GRUB, it gives me a screen that says "Ubuntu is running in low-graphics mode: your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself"

It was working just fine before I started to uninstall those programs. I think that I might have uninstalled something necessary to the system. If I click OK on the screen, it gives me options to reconfigure, troubleshoot, exit to console, or restart X. But no matter what I choose I still can't boot into ubuntu - I get stuck looking at the splash screen which stalls forever.

Any suggestions?
Thanks!

---

### Post by tekkidd on 2011-01-07
Simple Fix: Reinstall Video Drivers

---

### Post by zacharyh on 2011-01-07
Thanks for the quick reply!

Sorry but I'm pretty new to Ubuntu and Linux so how would I go about doing that? 

Thanks!

---

### Post by Bucky Ball on 2011-01-07
System->Admin->Additional Drivers.

Anything there that's now disabled? If so, 'Activate'.

Tekkid, by the post count Zacharyh is probably a new user. '... just reinstall video drivers' is not real helpful. ;)

---

### Post by zacharyh on 2011-01-07
Bucky Ball - thanks for the reply, but I can't seem to boot into Ubuntu to do as you instructed. And your correct, pretty new to ubuntu. :D

---

### Post by Bucky Ball on 2011-01-07
> **zacharyh said:**
> Bucky Ball - thanks for the reply, but I can't seem to boot into Ubuntu to do as you instructed. And your correct, pretty new to ubuntu. :D

Can you get to the screen where it lists the kernels? If so, boot into recovery kernel which should be second on the list. You will eventually get to some repair options. From there you can choose to boot in using Gnome-failsafe graphics mode (you'll find it there somewhere. Once in there, if you get that far, do what I suggested in last post.

a zillion ideas here:

[http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ac6lzq8-dhwz&ie=UTF-8&sa=Search&q=ipod+touch+Ubuntu&hl=en](http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ac6lzq8-dhwz&ie=UTF-8&sa=Search&q=ipod+touch+Ubuntu&hl=en)

... although you've probably tried a lot of them.

---

### Post by zacharyh on 2011-01-07
I've been searching google for some answers but so far no luck.

I can get into recovery mode some of the time, and if I use failsafeX (the fourth option) the Ubuntu is running in low-graphics mode message pops up again and the same problem above persists. 

EDIT: after the message appears it tells me to start in low-graphics mode for a session, reconfigure, troubleshoot, exit to console, or restart X. If I choose start in low-graphics it says "stand by one minute while the display restarts" but nothing happens.

---

### Post by Bucky Ball on 2011-01-08
See if you get the same issues with 10.04 LTS. Stabler and longer support time (until April 2013).

There are known issues and bug reports for 10.10 at the moment.

---

### Post by zacharyh on 2011-01-08
> See if you get the same issues with 10.04 LTS. Stabler and longer support time (until April 2013).

I hope I don't have to reinstall my once stable ubuntu installation in order to fix my problem, that would be my last resort...

---

### Post by Bucky Ball on 2011-01-08
True. Have you done any updates lately? In a terminal, could you type:

```
uname -r
```And that will show you what kernel you are using. What is it?

You could try System->Admin->Synaptics Package Manager->Edit->Fix broken packages. Should tell you if you have any along the bar at the bottom.

Also, open a terminal and try this:

```
sudo apt-get update
```then:

```
sudo apt-get upgrade
```This will NOT upgrade the kernel or OS to the newest, just the packages you are already using if there is a newer version (including vid drivers).

---

### Post by zacharyh on 2011-01-08
Um, I can't get into ubuntu at all, not even in low graphics mode.

Thanks for your support though!

---

### Post by Bucky Ball on 2011-01-08
Can you get to the menu list when you boot? Can you choose recovery kernel second on the list? If you're not getting this list, start hitting shift at boot and that should get you there.

---

### Post by zacharyh on 2011-01-08
A buddy I know was taking a look at my computer and he did something with the LiveCD, but now when I try to boot ubuntu I just get stuck looking at the splash forever.

Not sure what this means :/

---

### Post by zacharyh on 2011-01-08
> I can get into  recovery mode some of the time, and if I use failsafeX (the fourth  option) the Ubuntu is running in low-graphics mode message pops up again  and the same problem above persists. 

EDIT: after the message appears it tells me to start in low-graphics  mode for a session, reconfigure, troubleshoot, exit to console, or  restart X. If I choose start in low-graphics it says "stand by one  minute while the display restarts" but nothing happens.                                                                                                                   

I really can't get into ubuntu regardless

EDIT: Yes I see the GRUB menu with Ubuntu, Ubuntu Recovery, and Windows

---

### Post by Bucky Ball on 2011-01-08
. posted in error.

---

### Post by Bucky Ball on 2011-01-08
Have you tried booting into an earlier kernel if you have one on there? I may have asked this but getting tired. ;)

---

### Post by zacharyh on 2011-01-08
No previous kernels are displayed - and no problem, thanks for your continuous help :)

---

### Post by Bucky Ball on 2011-01-08
No worries. Running out of ideas but will keep thinking. ;)

---

### Post by zacharyh on 2011-01-08
I think I'll just opt for a clean install - I have a LiveCD handy :P Thanks for your help, but it seems me and my friend messed it up good. No problem - you live and learn I guess.

---

