---
title: "new life for old computer"
date: 2012-06-26
forum: General Help
---

### Post by GreatDanton on 2012-06-26
Hi, 
since support for 10.04 version will be over, I wanted to re-install system to lubuntu 12.04 (because of old computer). The problem occured during the boot, because everytime I would like to boot I get black screen. I know it's graphic card problem, since I always have this kind of problems with this old laptop.

Currently I have installed xubuntu 10.04, but i have to add this line:
etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

This is only working on old kernels (10.04, 10.10). However this trick doesn't work on the newer ybuntu operating systems. If i make this sometimes I am able to log in sometimes I am not. So does anybody know how to solve this problem? Any other ideas for other operating systems. I tried puppy linux, but i wasn't satisfied. I also tried debian lxde and I didn't like it. I would like to stay with Ubuntu operating system or something that uses the same commands like Ubuntu. Any ideas?

OK so here are my computer specifications
Dell inspiron 1100
512 MB ram
40Gb hdd
82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device <------Graphic card

I think now you have all informations you need.

Thanks in advance.

---

### Post by dino99 on 2012-06-26
i suppose its a fresh installation, without xorg.conf (not needed with actual kernel as this conf file often push conflict).

but you should pay attention at the graphic driver used and its activation (sudo jockey-gtk); maybe purge and reinstall it.

i suppose you have xserver-xorg-video-radeon installed from archive, not catalyst

boot on recovery mode and watch your logs (~/.xserver-errors & /var/log/)

---

### Post by sudodus on 2012-06-26
+1 for *dino99*'s suggestions

and I would like to add the following for the first part of the boot: try some other boot options, for example **[FONT="Courier New"][SIZE="3"]nomodeset[/SIZE][/FONT]**. I suggest that you test it booting from a CD or USB drive before entering it into your grub configuration.

[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

and the following for the flavour of Ubuntu: Lubuntu's ultra light desktop environment LXDE really makes old computers nice again.

---

### Post by GreatDanton on 2012-06-26
Thanks for the great suggestions.
However I didn't understand dino99 at all. Can you explain a little bit more about what to try out (I use Ubuntu for some time, but I am not the expert ;) )

> and the following for the flavour of Ubuntu: Lubuntu's ultra light  desktop environment LXDE really makes old computers nice again.

I was really surprised about that. My old computer was fast enough to do most of the job done-like internet, office and so on.

---

### Post by GreatDanton on 2012-06-26
I made like you suggested sudodus. Funny bit it works. It took some time to load, but it works.

So my line looks like this;
etc/default/grub

 GRUB_CMDLINE_LINUX_DEFAULT="no splash i915.nomodeset=1"


I will let you know if there will be any problems. Thanks for your help.

---

### Post by sudodus on 2012-06-27
I'm happy to help :-)

And when you feel that your problem is solved, please mark this thread as SOLVED

---

### Post by GreatDanton on 2012-06-29
Well, I experienced another problem. For example: when I try to install something (in this case Midori) via Lubuntu software center then Authentication window pop out. However this window is shaking so I am not able to click on it. After few second this window disappear. The result --> I am not able to install software, neither make changes via GUI (for example network manager).

Is it possible to solve this or not?

---

### Post by sudodus on 2012-06-29
What graphics driver is installed? Check with *dino99*'s suggestions in post #2

---

### Post by GreatDanton on 2012-06-29
I typed this in terminal: sudo jockey-gtk

this is the output:
```
(jockey-gtk:3765): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:3765): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

```

However no drivers are installed. Keep in mind this is old computer with integrated graphic card.

---

### Post by sudodus on 2012-06-29
Maybe you can change the screen resolution to something that works better.

Or try also some other boot option.

Edit: And you can try Knoppix, it is known to be good at hardware detection.

---

### Post by GreatDanton on 2012-06-29
Thanks I will definitely try knoppix. Which terminal commands you can use with knoppix, since I am most familiar with Ubuntu one :oops:.

Thanks for your help.

---

### Post by sudodus on 2012-06-29
Knoppix is based on debian linux and uses lxde. Originally it was made to run live, but now you can install it the normal way to an 'almost-debian' system. I have used Knoppix 6.4.4 that way.

You run bash as usual in the terminal, so the terminal commands are the same (provided that the programs are installed).

Is this answering your questions?

---

### Post by GreatDanton on 2012-06-29
Yes thank you. I will play a little with boot configurations and if will not work, then I will try knoppix or another distribution (hopefully debian based)

---

### Post by GreatDanton on 2012-06-30
I installed Knoppix. I am actually pretty happy with it, because it makes my laptop usable again. It's really lightweight (Knoppix uses only 55mb Ram), so it's suitable for old machines.

Even if the problem is not solved, because of the workaround, I can mark this thread as solved.

Thanks for your help.

---

### Post by sudodus on 2012-07-01
You are welcome,

I'm glad that I could help you :-)

---

