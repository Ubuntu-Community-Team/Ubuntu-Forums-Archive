---
title: "Catalyst for Ubuntu 10.04 64-bit and Switchable Graphics"
date: 2010-08-31
forum: General Help
---

### Post by Sup3r3g0 on 2010-08-31
I just got an HP dv7t Select Edition. I dual boot Windows 7 and Ubuntu. On Windows, I'm able to do a lot to customize graphics settings and switch from a mobility 5650 and the integrated Intel graphics to save battery life. So, I need help doing the same thing with Ubuntu.

Firstly, how do I correctly install the proprietary ATI drivers for Ubuntu 10.04 64-bit? I tried installing using the "restricted driver" pop up after first installing, but that caused my screen to go blank after rebooting. 

Furthermore, is there a way to switch graphics what graphics card I'm using? When I'm at home I like being able to use the dedicated card, but when I'm away and need to save power, I would like to be able to switch to the integrated card. I don't mind having some sort of option of selecting what card to use in the BIOS or something, although being able to switch on the fly would be nice.

Finally, if I make any changes, how do I undo them without having to reinstall?

Thanks for all the help. I appreciate it.

---

### Post by QIII on 2010-08-31
Don't know about switching.  I'll have to research.  Having two different OEM's cards may also be a part of the problem.

When you activated the proprietary driver, did you immediately go to the terminal and issue the following command

```
sudo aticonfig --initial -f
```

If not, you should be able to do it from recovery mode.  I think I had to do that once somewhere along the line when I forgot to initialize.

We might also have to take a look at whether others have had issues with your particular card.  I see some complaints about it with regard to the latest ATI driver available from AMD/ATI.  Installing CCC from the Lucid repo should get you Catalyst 10.4 (I believe), which is not the newest, but it is the one I have been using.

---

### Post by Sup3r3g0 on 2010-08-31
No, I didn't. Am I supposed to?

---

### Post by 3Miro on 2010-08-31
If you get a blank screen then you can hit Ctr + Alt + F1 and log into console mode to do the command
```
sudo aticonfig --initial -f
```
then reboot with
```
sudo shutdown -r now
```

If this doesn't help, then you can uninstall the driver with:
```
 sudo apt-get --purge remove xorg-driver-fglrx fglrx 
```
and then
```
 sudo dpkg-reconfigure xserver-xorg 
```
finally (and this may be an overkill, but just in case)
```
 sudo apt-get install --reinstall libgl1-mesa-glx libglu1-mesa  libgl1-mesa-dri 
```

I have never had trouble installing the driver, thought it never did much for me. Experience varies, but many people (myself included) have trouble with ATI + Linux combination. If I were you, I would disable ATI from the bios and go Intel only (at least under Linux).



I have never had trouble installing the driver, thought it never did much for me. Experience varies, but many people (myself included) have trouble with ATI + Linux combination. If I were you, I would disable ATI from the bios and go Intel only (at least under Linux).

---

### Post by QIII on 2010-08-31
Yes.  It's documented, but not really in a manner that jumps out in your lap and licks your nose if you don't know you should be looking for it.

---

### Post by 3Miro on 2010-08-31
In this case the problem might be with compatibility between the Catalyst driver and the hybrid graphics, not specific to ATI at all.

---

### Post by QIII on 2010-08-31
> **3Miro said:**
> Experience varies, but many people (myself included) have trouble with ATI + Linux combination. If I were you, I would disable ATI from the bios and go Intel only (at least under Linux).

On the other hand, many people (myself included) have had no trouble.  As you say, mileage may vary.

---

### Post by Sup3r3g0 on 2010-08-31
Thanks for all the help. I haven't been able to successfully install it yet. I had to delete the xorg.conf file to get rid of the black screen after booting up, but now I can get back to my regular desktop.

However, I'm still having problems with xterm and booting into recovery mode. Even before attempting to install the proprietary drivers, I was not able to get to xterm by using ctrl alt delete. My screen would sort of change colors around the corners and then nothing would happen. If I try and boot into recovery mode, I just get a blank screen. Is this a problem related to my graphics card?

---

### Post by 3Miro on 2010-08-31
Ctr + Alt + F1 (not delete). This is one difference between Linux and windows. Also, when you do that, you don't get a nice windows with xterm in it, you get a black screen with a blinking cursor like DOS (except you have way more control and capabilities then you ever did with DOS).

I am not sure why you cannot get into recovery mode, I would try reading about hybrid graphics and Linux (use Google).

---

### Post by Sup3r3g0 on 2010-08-31
Sorry, I meant to type F1. But still, xterm doesn't work and recovery mode gives me a blank screen.

---

### Post by sneax on 2010-10-06
I have exactly the same problem. CTR ALT F1 does not work either, the screen is blank and it will stay blank. Recovery mode goes blank too.

This is very hard to find information about, i have reinstalled numerous times with all kinds of "fixes" but none works. And I have to reinstall each and every time because i cant even get to a basic command prompt once i get the black screen of death!!! I need fglrx for gaming.

I have a HP tm2

---

### Post by httpitis on 2010-10-18
I have an Acer TimelineX 3820TG with switchable graphics (Intel GMA HD and ATI 5650).

If your bios has a setting to select graphics card, try setting it to Discreet instead of Switchable.

This was how I got the proprietary drivers to work anyway.

---

