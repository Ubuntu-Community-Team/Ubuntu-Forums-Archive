---
title: "ubuntu natty mini corrupted my pc"
date: 2011-06-02
forum: General Help
---

### Post by yeappp on 2011-06-02
Please please help did a install of ubuntu mini natty all went well with the install system went to reboot after succufull install then hangs 
other details on power up fan justspins
cursor just flashing
pressed e to try and enter grub no response
held down shift no response
held down shift and f1 no response

 i read on the posts something about a recovry i cant even get ito that
no cd of any other ubuntu i olny have the mini natty ubuntu which now i regretever trying to install in the first place it suppose to be minimal but the amount ofproblemsithas caused please help find a work around so i can use my pc again if you need further info please ask 

thank help getmy pc working again

---

### Post by mike555 on 2011-06-02
You do realize that most mini installs are CI only (command line)that means no desktop interface ??

---

### Post by yeappp on 2011-06-02
No i didnt reliase it doesnt state this on the ubuntu mini page but that does not explain why im getting a black screen with just a cursor flashing why cant i enter any commands whys the fan just spinning and not stoping?



what do i do from here to login to ubuntu what comand are you refering to to login if it is cl only

ok can you please give me some instructions on what to do what to input thanks

---

### Post by yeappp on 2011-06-03
Bump

---

### Post by romis on 2011-07-23
Hi!

I have your solution, as I've run into this problem in the past.

The Mini installer does normally install a CLI-only environment (unless you select any of the presets) and in previous versions it would take you to a CLI login prompt.

But due to a bug, which I've filed here: [https://bugs.launchpad.net/ubuntu/+bug/775279](https://bugs.launchpad.net/ubuntu/+bug/775279) it seems Natty will not boot without a graphical login screen. This is a shame, since I do like to install CLI-only screens.

Anyway, here's the fix.

Reboot your computer and press ESC a few times until you see the GRUB bootloader prompt. Choose the option with (recovery mode) in it, and then choose to continue normal boot when prompted.

Then you'll get the login screen you *should* be getting. Login with your username and password.

You'll need to install a graphical login manager. First install xorg which is what all of the graphical user interfaces are built on top of:

```
sudo apt-get install xorg
```

then install a login manager. You have a few options:

```
sudo apt-get install gdm
```
for GDM, which is GNOME's login manager. You may also need metacity otherwise your mouse cursor will not show up.

```
sudo apt-get install kdm
```
for KDE's login manager.

```
sudo apt-get install lxdm
```
For LXDE's login manager

```
sudo apt-get install lightdm
```
For LightDM, the desktop-independent login manager set to become the default in Ubuntu. 

You can also use others, for example

```
sudo apt-get install xdm
```
For the most simple of all of them, though it doesn't have many features the others do.

```
sudo apt-get install slim
```
For the SLiM login manager, which is pretty lightweight though requires configuration in text files sometimes.

There are a few others, you can read about on Wikipedia: [http://en.wikipedia.org/wiki/X_display_manager_%28program_type%29#Some_implementations](http://en.wikipedia.org/wiki/X_display_manager_%28program_type%29#Some_implementations) (note that some of those may not be in the repositories.)

Once that's installed you should install a desktop environment or window manager. For example:

```
sudo apt-get install ubuntu-desktop
```
This will install Ubuntu Desktop and all the packages and settings for it.

Replace ubuntu with xubuntu, kubuntu, xubuntu, or lubuntu for alternatives.

Note that you can also install the desktop environments without Ubuntu modifications.

```
sudo apt-get install xfce4
```
This will install Xfce without the Xubuntu modifications. It doesn't come with a web browser for example, so you'll have to install one like Firefox, Chromium, Epiphany, or Midori.

But anyway, once you have a desktop environment or window manager of some kind as well as a login manager reboot your computer with the following command:

```
sudo shutdown -r now
```
(or you can run ```
sudo reboot
```)

And you'll be able to login.

---

