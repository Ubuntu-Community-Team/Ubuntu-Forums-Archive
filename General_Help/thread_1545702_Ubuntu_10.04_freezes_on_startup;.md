---
title: "Ubuntu 10.04 freezes on startup;"
date: 2010-08-04
forum: General Help
---

### Post by Innuendo108 on 2010-08-04
Yesterday I reinstalled my Ubuntu OS, and the whole day I was using it successfully.
Tonight I turn on my notebook - Ubuntu started but when gnome started - it freezed. I can see all my environment: desktop, panels, prompt for password for internet but it freezed - i can't click on anything by my mouse and if I press something on keyboard - nothing happens.

I tried to open OS in recovery mod. It wrote to me:
> 
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 184902/1313280 files, 990550/5242880 blocks
fsck from util-linux-ng 2.17.2
/dev/sda5: recovering journal
/dev/sda5: clean, 11044/5251072 files, 12258042/20972849 blocks
init: fail to start ....

the last string i do not remember exactly.

After a fews tries to open recovery mode, it opened recovery mode. I've chosen normal start and then in console I've typed:
sudo /etc/init.d/gdm start
And gnome opened but FREEZED again.

How can I fix this problem? help me please;
My Laptop is ACER 5620:
> 
Chipset Intel PM965 Express
CPU Intel Core 2 Duo 1.5 &#1043;&#1043;&#1094;
RAM: 2GB DDR2
Video: ATI Mobility Radeon X2400-XT 256 &#1052;&#1073;


---

### Post by chopinhauer on 2010-08-04
> **Innuendo108 said:**
> 
the last string i do not remember exactly.


Sorry, but that string is the important part. :-) However, it seems it repaired itself.

> **Innuendo108 said:**
> 
sudo /etc/init.d/gdm start
And gnome opened but FREEZED again.


I understand the login screen appeared, but then mouse and keyboard freezed? No way to return to a console with CTRL+ALT+F1? My guess is that something is wrong with 'gdm', try reinstalling it:
```
sudo apt-get --reinstall install gdm
```

---

### Post by Zorgoth on 2010-08-04
It could well be a graphics issue; what drivers are you using?

---

### Post by StewartM on 2010-08-04
Does it have a graphics chipset on the motherboard?

You may want to look at the following sites.

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

There is also a thread going (81 pages so far!) of people experiencing the same issues.

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

StewartM

---

### Post by Innuendo108 on 2010-08-04
> **chopinhauer said:**
> 
I understand the login screen appeared, but then mouse and keyboard freezed? No way to return to a console with CTRL+ALT+F1? My guess is that something is wrong with 'gdm', try reinstalling it:
```
sudo apt-get --reinstall install gdm
```


No, I do not have login screen - I have autologin. It opens whole system - I see desktop, panels, Gnome Do and Prompt for password for internet (it is always been asked on startup).

When I made sudo /etc/init.d/gdm start - and opened system, CTRL+ALT+F1 works (only this works, other shortcuts - no). and console opens again. ALT+F7 returns to Gnome, but in freezed.


---------

I use proprietary graphic for ATI. I 've always used it. I have this laptop for a year, and it worked fine with Ubuntu 9.04, then with Ubuntu 9.10 and then in Ubuntu 10.04. Always had proprietary driver for ATI (system offers this driver itself)

---

### Post by linux18 on 2010-08-04
-choose recovery mode at grub
-drop to a root prompt 
-type "telinit 3" and logon
-type "xinit" 
-after it loads type "metacity &" (you may need to wiggle the mouse   before it registers)
-then type "gnome-panel & nm-applet &"
your good to go! a reboot will take you back into the normal DE

---

### Post by filip007 on 2010-08-04
Install again and don't use or disable any desktop effects like 3D and so on.

Maybe is also problem with power management and waking up on your laptop.

---

### Post by chopinhauer on 2010-08-04
> **Innuendo108 said:**
> 
When I made sudo /etc/init.d/gdm start - and opened system, CTRL+ALT+F1 works (only this works, other shortcuts - no). and console opens again. ALT+F7 returns to Gnome, but in freezed.


There is freezed and **freezed**, I believe your problem is in the first category.

If you can move the mouse, but the windows don't have borders, probably **metacity** crashed (the Window Manager). You can restore it with:
```
DISPLAY=:0 metacity --replace
```in a terminal.

Or just the panel froze. Kill it and run it again:
```
killall gnome-panel && DISPLAY=:0 gnome-panel
```

---

### Post by Innuendo108 on 2010-08-04
2 linux18
i've tried. It opened an x-session, but after reboot it opens my gnome and frozen (i can move my mouse but i can't click on anything)

---

### Post by celldweller1591 on 2010-08-04
have you tried acpi=off yet ?

---

### Post by Innuendo108 on 2010-08-04
2 chopinhauer
Thank you. This message I write from my normal Ubuntu session.

I've log in recovery mode, typed:
sudo /etc/init.d/gdm start
Than I press CTRL+ALT+1 again
and typed:
DISPLAY:=0 metacity --replace
sudo /etc/init.d/gdm restart

And then opened gnome - not frozen. I haven't reboot yet, but I think, it will work well.

ALSO, I've noticed that I donot have LOAD screen (violet screen with ubuntu label and five-ball progress-bar) while ubuntu is loading...
Early i had this screen.

---

### Post by Innuendo108 on 2010-08-04
I've hurried Up.
After reboot it freezes again. =((

I think I'll reinstall my Ubuntu, and in future I'll be more attentive with installing compiz/3d and other effects.

---

### Post by chopinhauer on 2010-08-04
> **Innuendo108 said:**
> 
I think I'll reinstall my Ubuntu, and in future I'll be more attentive with installing compiz/3d and other effects.

When you are in your unfrozen session, you can just deactivate your desktop effects: Preferences > Appearance and then check if putting them again crashes compiz.

Or you can purge compiz:
```
sudo apt-get --purge remove compiz
```
and install it again:
```
sudo apt-get install compiz
```

---

