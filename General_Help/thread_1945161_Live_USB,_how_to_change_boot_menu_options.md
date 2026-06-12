---
title: "Live USB, how to change boot menu options?"
date: 2012-03-22
forum: General Help
---

### Post by gypsumwolf on 2012-03-22
When using L/K/Ubuntu as a Live USB, how can I change the boot options where it says "Try ubuntu..."? Where is that text string in grub2?

---

### Post by gypsumwolf on 2012-03-23
<bump>

---

### Post by dragonfly41 on 2012-03-23
I'm not sure what you're trying to do .. but when you are launched into ubuntu desktop launch Synaptic Package Manager and search "customizer"

there is ..

**grub-customizer**

and ..

**[COLOR=black]uck[/COLOR]** - tool to customize official Ubuntu Live CD's


[Edit]  I assume you've booted up while pressing F12 to select "boot from USB"?

[http://askubuntu.com/questions/101503/unable-to-boot-ubuntu-11-10-from-external-usb-drive](http://askubuntu.com/questions/101503/unable-to-boot-ubuntu-11-10-from-external-usb-drive)

---

### Post by gypsumwolf on 2012-03-26
What I am trying to figure out is, when I use UCK on a Live CD while in the console how do I change the boot menu that traditionally shows up when you insert a Live CD or Live USB. This menue is the one that pops up right as you boot from the CD or USB. (Like "Try ubuntu without installing" and "Install Ubuntu" and "Check disc for defects"...) How do I change those menu options?

For instance, if I want to (using UCK) change "Try ubuntu without installing" text string to just "Ubuntu Live" using the console.

---

### Post by gypsumwolf on 2012-03-26
Can this be done using grub-customizer in the UCK console? If so that would be cool, but I am looking for the manual way to do it.

---

### Post by dcstar on 2012-03-27
> **gypsumwolf said:**
> When using L/K/Ubuntu as a Live USB, how can I change the boot options where it says "Try ubuntu..."? Where is that text string in grub2?

/boot/grub/loopback.cfg

The 12.04 Beta Live USB is impressively fast booting and shutting down.

---

### Post by mastablasta on 2012-03-27
note that any changes made in live system are lost at reboot.
 
That is unless you are trying ot make your own distribution.

---

### Post by gypsumwolf on 2012-03-27
> **mastablasta said:**
> note that any changes made in live system are lost at reboot.
 
That is unless you are trying ot make your own distribution.

If I use UCK then it should not be lost. Also It should not be lost if I use a persistence file.

---

