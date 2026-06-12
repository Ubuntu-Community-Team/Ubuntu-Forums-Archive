---
title: "Ubuntu dual boot broken with upgrade"
date: 2011-08-15
forum: General Help
---

### Post by helpme123456 on 2011-08-15
I had been running a dual boot of both ubuntu and windows 7. I recently upgraded to ubuntu 11.04. After doing so i no longer have the option to select to load windows from the grub loader. Instead of the options presenting themselves my screen remains black before loading ubuntu. Any help would be much appreciated.

---

### Post by helpme123456 on 2011-08-15
bump

---

### Post by Quackers on 2011-08-15
Have you run ```
sudo update-grub
``` in your new installation? What does it give?

---

### Post by helpme123456 on 2011-08-15
> **Quackers said:**
> Have you run ```
sudo update-grub
``` in your new installation? What does it give?
got the following 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda3
done
tom@tom-G5200uk-m:~$

---

### Post by Quackers on 2011-08-15
You should now get a grub menu when you reboot. If not, there is something else wrong. Please let us know.

---

### Post by helpme123456 on 2011-08-15
> **Quackers said:**
> You should now get a grub menu when you reboot. If not, there is something else wrong. Please let us know.
hmm confused. When i reboot i am greeted with a screen saying something is out of range, the screen can even go into standby, grub refuses to show. Is it possible it is loading but is not visible, graphics problem?

---

### Post by Quackers on 2011-08-15
It could be a graphics problem, but it's strange that it just started since running update-grub!
Or did you run some updates recently?
What graphics card are you running?

---

### Post by helpme123456 on 2011-08-15
> **Quackers said:**
> It could be a graphics problem, but it's strange that it just started since running update-grub!
Or did you run some updates recently?
What graphics card are you running?
It has only started since i completed the upgrade, i have been back on windows since then, only once though. I have no idea what graphics card i am running mate.

---

### Post by Quackers on 2011-08-15
So 11.04 has not been booted yet? That makes more sense.
It may be that you will need a boot option to get past your graphics problem.
It's difficult to say without knowing what your graphics card is. The nomodeset option works for ATI and Nvidia cards, often. It is usually only needed until the appropriate graphics driver is installed - via Additional Drivers being run.

The guide blow gives some details on boot options and how to use them. Make sure you are reading the section for installed systems (not wubi) and not the live cd/usb version.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by helpme123456 on 2011-08-15
> **Quackers said:**
> So 11.04 has not been booted yet? That makes more sense.
It may be that you will need a boot option to get past your graphics problem.
It's difficult to say without knowing what your graphics card is. The nomodeset option works for ATI and Nvidia cards, often. It is usually only needed until the appropriate graphics driver is installed - via Additional Drivers being run.

The guide blow gives some details on boot options and how to use them. Make sure you are reading the section for installed systems (not wubi) and not the live cd/usb version.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
sorry mate not tech savy at all, at the cost of sounding like a total dunce i really dont understand what to do

---

### Post by Quackers on 2011-08-15
I can't explain it any better than the originator of that thread does.
Scroll down to the section headed
"How to temporarily set kernel boot options on an installed OS (not wubi)"
and follow the instructions using the nomodeset option.
If it boots, run the Additional Hardware utility and install the graphics driver offered. If no driver is offered, scroll to the next section of that guide and make the nomodeset option permanent.

---

### Post by helpme123456 on 2011-08-15
> **Quackers said:**
> I can't explain it any better than the originator of that thread does.
Scroll down to the section headed
"How to temporarily set kernel boot options on an installed OS (not wubi)"
and follow the instructions using the nomodeset option.
If it boots, run the Additional Hardware utility and install the graphics driver offered. If no driver is offered, scroll to the next section of that guide and make the nomodeset option permanent.
so sorry mate for sounding like a complete fool but i recieved this message
The program 'linux' is currently not installed.  You can install it by typing:
sudo apt-get install user-mode-linux

---

### Post by helpme123456 on 2011-08-15
sorry just seen my **** up

---

### Post by Johnb0y on 2011-08-15
could try: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

this helped me with my xp/ubuntu issue... hope it helps you too :smile:

p.s. it is free for private use...

---

### Post by helpme123456 on 2011-08-15
just pressed shift after the bios menu, couldnt get into grub
message on screen says input signle oput of range
chnage settings to 1600*900 60Hz

---

### Post by helpme123456 on 2011-08-15
This is unbelievably frustrating, i have no idea what to do

---

### Post by helpme123456 on 2011-08-15
I am constantly receiving this message upon boot
input signal out of range change settings to 1600x900 60Hz?!?!?

---

