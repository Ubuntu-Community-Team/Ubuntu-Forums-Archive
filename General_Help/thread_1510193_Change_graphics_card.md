---
title: "Change graphics card"
date: 2010-06-15
forum: General Help
---

### Post by leehamer on 2010-06-15
Afternoon, 

For a while I have been using Ubuntu with my Nvidia graphics card, it was very old and finally died on me yesterday so I want to use my onboard graphics for the time being untill I replace the computer. Is there a way to get Ubuntu to boot in a safe graphics mode or something? When I boot with my old card removed I get some of the boot process showing but when it gets to the log in screen it displays a resolution my monitor doesnt support.

I am using 10.04

cheers for your help in advance

---

### Post by Irony on 2010-06-15
Something like this;

[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

```
sudo dpkg-reconfigure xserver-xorg
```

or this;

[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

---

### Post by philinux on 2010-06-15
> **leehamer said:**
> Afternoon, 

For a while I have been using Ubuntu with my Nvidia graphics card, it was very old and finally died on me yesterday so I want to use my onboard graphics for the time being untill I replace the computer. Is there a way to get Ubuntu to boot in a safe graphics mode or something? When I boot with my old card removed I get some of the boot process showing but when it gets to the log in screen it displays a resolution my monitor doesnt support.

I am using 10.04

cheers for your help in advance

Boot into recovery mode. Then ```
sudo apt-get remove nvidia-current
```

Assuming thats the driver you were using. The system should then revert the nouveau driver. I assume you've been into the bios to enable the onboard graphics.

---

### Post by leehamer on 2010-06-15
.. posted in error ..

---

### Post by leehamer on 2010-06-15
> **philinux said:**
> Boot into recovery mode. Then ```
sudo apt-get remove nvidia-current
```Assuming thats the driver you were using. The system should then revert the nouveau driver. I assume you've been into the bios to enable the onboard graphics.

Could you advise me on how to get into recovery mode? 

Thats the driver I was using, also I have enabled the onboard graphics. 

Cheers guys

---

### Post by r-mo on 2010-06-15
To get into recovery mode hold down the shift key just after the bios screen, it should bring up a menu to select recovery mode option.  As an alternative once the computer boots and you get the resolution unsupported error press ctrl+alt+F3 and that should take you to a terminal screen (hopefully with a supported resolution).  Then uninstall nvidia-common

```
sudo apt-get remove nvidia-common
```

and reconfigure xserver

```
sudo dpkg-reconfigure xserver-xorg
```

HTH

---

### Post by leehamer on 2010-06-15
Spot on.. all I needed to know, helpful as always :)

---

### Post by philinux on 2010-06-15
Let us know how you get on.

---

### Post by leehamer on 2010-06-16
I tried all that is mentioned above to no avail, I actually noticed last night when I was trying this that it doesnt actually say "unsuported resolution" but states "No signal" then my montitor goes onto standby.

I booted my 9.10 disc to check it wasnt a hardware issue with the onboard graphics and it ran fine. 

I tried to see if I could remove the drivers and reconfig the xorg file whilst using boot but this would not work. 

When the computer boots I get the BIOS screen, then a little line in the top left flashing before lines of code flash by on the top inch or so of my screen. This disapears then it just looses signal to the monitor. I am guessing this is because my computer still has the Nvidia drivers installed.

One thing i did notice is that when I turned the computer off by hitting the power on a couple of occasions I had an Ubuntu screen appear that said it was checking my harddrive as it did not shut down properly. 

Sorry if I am sounding dim but I my only Linux experience is since the day 9.10 became available and I dumped windows.. I am trying to avoid doing a fresh install though

---

### Post by leehamer on 2010-06-18
Any further advice??

---

