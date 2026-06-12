---
title: "Can't install Ubuntu on my computer"
date: 2011-06-04
forum: General Help
---

### Post by W33DY on 2011-06-04
Hi everyone :) I'm been traying to install Ubuntu for over 6 months but still didn't get it :( I'm getting really desesperate :(. So, I found this forum and I hope you can help me.
I boot it from a USB device and boots, but when it cames to install it crashes after the loading image.
THis is the image:[IMG]http://i54.tinypic.com/2u74mdh.jpg
THank you :)

---

### Post by Joe- on 2011-06-04
Are you booting in a virtual box? Because i can see win7 stuff in the picture?

---

### Post by W33DY on 2011-06-04
> **Joe- said:**
> Are you booting in a virtual box? Because i can see win7 stuff in the picture?

No, I'm not booting in a virtual box. I downloaded the .ISO image and burned it to a USB device. After that I restarted my computer and enter in the boot menu. It boots from the USB, loads the ubuntu installation and then crashes :(

---

### Post by Joe- on 2011-06-04
Im not sure about the crashing, have you considered using Wubi?

---

### Post by W33DY on 2011-06-04
> **Joe- said:**
> Im not sure about the crashing, have you considered using Wubi?

I already tried all possibilites :S I think i'm missing one thing. Maybe I need to create 2 partions before install ubuntu.

---

### Post by Joe- on 2011-06-04
When you boot from the .ISO can you check the disk for errors? Does it give you that option? And what happens if you just try and run Ubuntu rather than installing?

---

### Post by oldfred on 2011-06-04
What video card do you have?

I have nvidia and for the last few versions have had to add nomodeset for CD, USB and first boot after installing.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

---

### Post by W33DY on 2011-06-04
I have nvidia 8600GT, maybe it's the same problem as yours, i hope so. I think you save my life :)

---

### Post by linuxinstalledfromhdd on 2011-06-04
Check to see if you computer has "on-board" graphics, and then you can disable your other video card and switch your monitor to the on-board graphics svga port, and install your system with that for now.

---

### Post by LowSky on 2011-06-04
Ubuntu LiveCD or USB should create a scrambled screen of the Windows desktop...

Something else has to be at play.

---

### Post by W33DY on 2011-06-04
I'm almost to give up. I can't get it installed, always stop there. I even can't enter in the ubuntu menu. It shows this screen [IMG]http://www.absolutelytech.com/wp-content/uploads/2010/05/Screenshot.jpg[/IMG]
and i press F6, although nothing happens and it skips to this screen: 
[IMG]http://janusunderground.files.wordpress.com/2011/01/ubuntu-boot-image.png[/IMG]
and then... It crashes.

---

### Post by Joe- on 2011-06-04
Perhaps download a different versions of Ubuntu? Or create a new Disc Image.

---

### Post by W33DY on 2011-06-04
Ok, I tried again and in the "Ubuntu boot menu" I tried to press F6 but nothing happens. The screen only blinks.

---

### Post by jamesisin on 2011-06-04
As Joe suggests above, you may need to use a different installer than the usual installer.  There is an installer oriented toward non-Intel processors and one called Alternative or Alternate which has a very stripped down installer.  The regular installer is likely bumping into a driver it can't handle or some such.

---

