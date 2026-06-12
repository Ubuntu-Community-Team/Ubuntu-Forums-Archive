---
title: "Display Problem"
date: 2011-03-08
forum: General Help
---

### Post by Gtown209 on 2011-03-08
Hello, I currently have a nvida 6800 gt using dvi-hdmi to a phillips 42 inch hdtv.

When I boot the live ubuntu 10.10 using my usb I can't see all of the desktop, the border or edges are cut off the screen, how can I fix this problem?

---

### Post by Hedgehog1 on 2011-03-08
> **Gtown209 said:**
> Hello, I currently have a nvida 6800 gt using dvi-hdmi to a phillips 42 inch hdtv.

When I boot the live ubuntu 10.10 using my usb I can't see all of the desktop, the border or edges are cut off the screen, how can I fix this problem?

Hello!

Menu to System >> Administration >> Nvidia X server settings.

In the second to last item in the list, you will find an 'Overscan Compensation' slider. Adjust it until you can see the whole screen on the TV.

***The Hedge***

:KS

---

### Post by mikewhatever on 2011-03-08
You could try changing the resolution, but on the other hand, I don't think live CDs were intended to output to 42 inch displays.

---

### Post by Hedgehog1 on 2011-03-08
Actually, the LiveCD will work on an HDTV if you are connected via a real HDMI out of the PC's GPU.  It doesn't fill the screen, but you have everything you need to get by...

I really don't know HOW I lived before I had my 55" HDTV as my monitor...

***The Hedge***

:KS

slowing going blind....

---

### Post by mikewhatever on 2011-03-08
That's a really huge monitor, Hedgehog1.:D

---

### Post by Gtown209 on 2011-03-08
When I go to the nvidia control settings, it says "You do not appear to be using the NVIDIA X driver. Please edit your X configureation file (just run 'nvidia-xconfig' as root), and restart the x server.

nvidia-xconfig shows Unable to locate/open x configuration file

I don't see "In the second to last item in the list, you will find an 'Overscan  Compensation' slider. Adjust it until you can see the whole screen on  the TV."

Will nvtv tv out fix it?

---

### Post by Hedgehog1 on 2011-03-08
You will want the nvidia driver setup.

Do a
```
sudo nvidia-xconfig
```
To get it setup and then reboot.

You do not have to use an HDMI cable.  If you are routing your sound out of the PC directly your amp, the DVI cable is fine.

***The Hedge***

---

### Post by willhurley82 on 2011-03-08
Another thing you may want to try (this worked with my 42" lcd t.v.) is to check and see if your screen is in fullscreen, stretch, etc., on the television itself.

---

### Post by Hedgehog1 on 2011-03-08
> **willhurley82 said:**
> Another thing you may want to try (this worked with my 42" lcd t.v.) is to check and see if your screen is in fullscreen, stretch, etc., on the television itself.

Well, <sniff> if you want to take the sissy way out, <sniff> you can try that, too. :D

---

### Post by Gtown209 on 2011-03-08
> **Hedgehog1 said:**
> You will want the nvidia driver setup.

Do a
```
sudo nvidia-xconfig
```To get it setup and then reboot.

You do not have to use an HDMI cable.  If you are routing your sound out of the PC directly your amp, the DVI cable is fine.

***The Hedge***


Thats what I did sudo nvidia-xconfig and it shows something like nvidia-xconfig shows Unable to locate/open x configuration file,

I even did service gdm stop and tried running the command

---

### Post by Hedgehog1 on 2011-03-08
Time to reinstall the nvidia drivers, then:

System >> Administration >> Additional Drivers

---

### Post by mikewhatever on 2011-03-09
Keep in mind, the OP is running from CD, and must be using the nouveau driver, and not the proprietary nvidia driver.

---

### Post by Hedgehog1 on 2011-03-09
> **Gtown209 said:**
> 
**When I boot the live ubuntu 10.10 using my usb** I can't see all of the desktop, the border or edges are cut off the screen, how can I fix this problem?

mikewhatever,

Yup - I forgot that.  Sorry Gtown209, I got a little carried away.  If you have an HDMI cable, you may have better luck with that - but without the NVidia drivers running I cannot promise anything.

***The 'excitable' Hedge***

:KS

---

