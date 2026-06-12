---
title: "How to downgrade to vesa"
date: 2010-05-26
forum: General Help
---

### Post by justgoodin on 2010-05-26
Hi, I am a complete newbie to Ubuntu, and i have an Intel graphic chipset

```
lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE 
Chipset Integrated Graphics Device [8086:2562] (rev 03)
```

I have been hounded by frequent lockups and flickering screen, i get a message "checking battery state" or something like that, after which the screen gets currupted and it flickers.

So, after viewing the Lucid Freeze fixes at wiki.ubuntu, i felt the problem is with the grafix driver.

SO although i want to downgrade to vesa drivers, but i can't even fine my xorg.conf file,(it is not where they said it would be "/etc/X11/xorg.conf"


So can someone please give me a step by step instruction to switch to vesa? (And please don't forget I'm a newbie to ubuntu.):(

---

### Post by Grenage on 2010-05-26
xorg.conf isn't normally required in Ubuntu, but if you create one it will be used.  I have a rough guide [here]("http://www.grenage.com/xorg.html").

Basically, you'll just need to use *vesa* when specifying the driver.

---

### Post by Sylos on 2010-05-26
Quite the newb myself here....but..... cant you just go into the system menu and then the restricted drivers page and switch from there?

---

### Post by justgoodin on 2010-05-27
> **Sylos said:**
> Quite the newb myself here....but..... cant you just go into the system menu and then the restricted drivers page and switch from there?

errmm!!! i can't find any restricted drivers section in system menu!!!:(

---

### Post by Catharsis on 2010-05-27
```
gksudo gedit /etc/X11/xorg.conf
```
Then just copy and paste :)

---

### Post by Sylos on 2010-06-09
Are you still trying to fix this up?

Im not using Lucid so im not sure what the name would be in the System menu but there is usually something Like 'Hardware' that would allow you to switch on and off the accelerated hardware options. I thought this might help (maybe?).

If you need help trying to sort out and Xorg.conf file I can try to help with that as I had to change one myself a while ago due to failure to recognise hardware.

Post again if you havent already sorted it (i'll try to reply quicker this time).

---

### Post by tommcd on 2010-06-09
> **justgoodin said:**
> 
I have been hounded by frequent lockups and flickering screen, i get a message "checking battery state" or something like that, after which the screen gets currupted and it flickers.

Are you trying to use compiz and the desktop effects? If so, then first try turning off all desktop effects and see if that helps.
Go to: system > preferences > appearance > desktop effects tab. Click the button for None.

You will likely not be happy with the minimal performance of the vesa driver.

---

### Post by RJQ on 2010-06-10
Unfortunately none of this methods is going to work, this is a well known problem with the xorg driver linux-wide, no distro is safe from this. is either sticking with lucid and low performance and or crashes or using a older version of linux/ubuntu.

---

### Post by justgoodin on 2010-07-26
Thank you all for the help. I finally managed to edit the Xorg.conf file.

And no, it did not fix the problem, but the latest glasen-ppa fixes listed at [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) did do the job :)

---

