---
title: "Black login screen on 10.10 (weird problem)"
date: 2010-12-28
forum: General Help
---

### Post by ELCouz on 2010-12-28
Hi,
I've been using Ubuntu 10.10 for a while it is so great! :)

But for the first time, I've booted my laptop on battery power instead of AC power.

I have a black screen on the gnome login and i can hear the ubuntu sound. If i press CTRL+ALT+F2 the screen switch from black to the login (terminal version).

The problem only appear when i boot from battery power...if i boot from AC power everything is fine !!! I can see the gnome login page ... in fact i've reinstalled ubuntu same problem.

I think it's a bug with the release.

My laptop is a HP TX2000.

Please help me, a laptop without battery support is useless !!! :(

regards,
laurent

---

### Post by coldraven on 2010-12-29
I don't know if this helps but when you get to the black screen have you tried moving the cursor about. When my laptop resumes from suspend I have to do that before I can see the login box.

---

### Post by Mark Phelps on 2010-12-29
I've encountered this time and time again -- and I'm NOT using a laptop -- and only on version 10.10.

What I've had to do to "fix" it (I put "fix" in quotes because it is not permanent), is the following:
1) Boot into GRUB selecting the Recovery Mode
2) Select the option to repair broken packages
3) When done, and the prompt is back, enter "startx"

That usually gets me a desktop and when I then reboot, the next time, I get a regular desktop screen -- until a few days later, when this starts all over again.

I tried to raise this as a concern a while back, but I got so soundly "thrashed" for DARING to criticize Ubuntu 10.10 that I've not brought it up since.

---

### Post by ELCouz on 2010-12-29
Hi,
Thanks for your replies!

No luck with the solutions provided in the thread :(

The problem i'm experiencing is a current bug on Ubuntu 10.10.
Sadly no one picked up the project to fix the bug yet :(
On older linux kernel it seems to work ... kind of a regression bug.

Here's more info: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578119](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578119)


I think maybe a temp (dirty) workaround would be to trick the kernel that the laptop have AC power connected when booting from the battery...

EDIT: temp workaround...

> when the screen is black switch to tty1 CTRL+ALT+F1 , login then

sudo /etc/init.d/gdm restart

it should restart gnome and everything should be fine until the next battery power boot (repeat each boot).


best regards,
laurent

---

### Post by ELCouz on 2010-12-29
Bug has been fixed with kernel v2.6.37-rc2-maverick.

For people having this issue (paste this in the terminal)

```

wget kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/linux-headers-2.6.37-020637rc2-generic_2.6.37-020637rc2.201011160905_i386.deb
wget kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/linux-headers-2.6.37-020637rc2_2.6.37-020637rc2.201011160905_all.deb
wget kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/linux-image-2.6.37-020637rc2-generic_2.6.37-020637rc2.201011160905_i386.deb
sudo dpkg -i linux*.deb

```

once finished... 
```
sudo shutdown -r now
```
To restart with your new kernel

regards,
laurent

---

### Post by Jinda on 2011-01-27
Will try it out tonight. Thanx

---

### Post by Jinda on 2011-01-28
> **Jinda said:**
> Will try it out tonight. Thanx

Unfortunately system now boots to terminal

---

### Post by mastablasta on 2011-01-28
try 
 
startx 
 
to start the GUI.

---

### Post by Jinda on 2011-01-28
> **mastablasta said:**
> try 
 
startx 
 
to start the GUI.

I did. The log says screen found but no usable config.

---

### Post by waspbr on 2011-01-29
hmmm, I have a similar issue on my hp tx1320us and also on the tx2100ed. 

long story short, I cannot offer you a fix but a workaround, mostly a way to login.

boot as usual,then when you should get to the GDM the screen goes black, you should hear whatever login sound it makes. What you do here is press 

```
CTRl + ALT + F1
```

you can either press F2, F3, F4, F5 or F6. it doesn matter. it should then bring you to a terminal login prompt, right?

Then Press, 


```
CTRl + ALT + F7
```

this should take you right up to the gui.

---

### Post by Jinda on 2011-04-01
I have given up on Maverick on my laptop and done a clean install of Lucid which works fine withou hitches. I think there is a regression in the display manager. In Maverick my systems lags, and freezes. I have to move the mouse about for the system to respond. The system also fails to shutdown properly and freezes. It only responds when you press the power button. Maybe better luck in Natty

---

