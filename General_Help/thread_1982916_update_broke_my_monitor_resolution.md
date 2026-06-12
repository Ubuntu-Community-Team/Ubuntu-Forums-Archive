---
title: "update broke my monitor resolution"
date: 2012-05-19
forum: General Help
---

### Post by unused_bagels on 2012-05-19
I try to change my monitor resolution, and the max is will allow is 1024.  xrandr doesn't think I have VGA anymore.  I'm using a GeForce 8400 with a max output of 1600x900.  I tried adding the mode to xrandr but it said my max allowable was 1024.  Here's some code:
```
    user@Mr:~$ lspci | grep VGA
    02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
    user@Mr:~$ xrandr
    xrandr: Failed to get size of gamma for output default
    Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
    default connected 1024x768+0+0 0mm x 0mm
       1024x768       61.0*
       800x600        61.0  
       640x480        60.0

```
I'm running 11.10 and am not ready to update to Precise yet on this box.

---

### Post by bodhi.zazen on 2012-05-19
What driver are you using ?

---

### Post by unused_bagels on 2012-05-19
It says,
Driver: VESA: G98 Board - 06910011
Experience: Standard

---

### Post by bodhi.zazen on 2012-05-19
Try the nouveau driver or install the nvidia driver. Are you using a custom xorg.conf ?

---

### Post by unused_bagels on 2012-05-21
synaptic says I have the nouveau driver (experimental).  NVidia's website says I have to stop X and nouveau to install their driver, and give me a dissertation on how to do it.  There has to be an easier way, every time I quit X with 
```
sudo service lightdm stop
```
or
```
sudo stop lightdm
```
I get a bunch of crap (black screen, some text sometimes) and no prompt.  
 
When I try to reboot and hit ESC, nothing happens, no grub menu or anything.  This is making me rather unhappy :mad:

---

### Post by bodhi.zazen on 2012-05-21
> **unused_bagels said:**
> synaptic says I have the nouveau driver (experimental).  NVidia's website says I have to stop X and nouveau to install their driver, and give me a dissertation on how to do it.  There has to be an easier way, every time I quit X with 
```
sudo service lightdm stop
```
or
```
sudo stop lightdm
```



That is NOT how you install the nvidia driver on Ubuntu.

See [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)


> I get a bunch of crap and no prompt.  
 
When I try to reboot and hit ESC, nothing happens, no grub menu or anything.  This is making me rather unhappy :mad:

That "bunch of crap" is information we need to help you.

Also keep in mind, updates sometimes fail. It is often easier to back up your data and do a fresh install (sorry about that).

---

### Post by unused_bagels on 2012-05-21
bodhi, that was it!!!! I don't know why NVIDIA doesn't just tell people to go to "Additional drivers" and manually install from there.  It turned out all I had to do was just re-install my driver from there, just like I did on first install.
Thank you!

---

### Post by bodhi.zazen on 2012-05-21
> **unused_bagels said:**
> bodhi, that was it!!!! I don't know why NVIDIA doesn't just tell people to go to "Additional drivers" and manually install from there.  It turned out all I had to do was just re-install my driver from there, just like I did on first install.
Thank you!

\o/

---

