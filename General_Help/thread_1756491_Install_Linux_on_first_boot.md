---
title: "Install Linux on first boot?"
date: 2011-05-12
forum: General Help
---

### Post by streetlightman on 2011-05-12
Hey all,

I was wondering if it was possible to put something like a linux image on to a hard drive to install the OS on first boot.  The reason I want to do this is because of the following reasons.  

First, I broke the IDE port on the mobo so I can't use the internal DVD drives on the computer.

Second, I don't have an extra SATA DVD drive lying around.

Third, for some reason, this computer will boot from a USB DVD drive but once it starts loading the kernel, it just stops calling the drive and the computer freezes.  I tested the disc and the drive with another computer and it works fine.

And forth, the computer refuses to boot from a USB flash drive with linux on it.

So as you can see, I'm in a bit of a pickle here.  I would love to be able to hook the hard drive up to another computer and put the required files on the it for it to boot up to an installation.

Thanks

---

### Post by Joe of loath on 2011-05-12
Yes, should be possible. Plug the disc into another computer, create a ~1gb FAT partition, and use unetbootin to burn an image to that partition. You will have to click the 'show all drives' box, so check where you're installing to at least three times, or you might kill your current install...

---

### Post by drs305 on 2011-05-12
If you are currently booting from a Grub2 menu, and you can download the Ubuntu ISO, you can install it. I'm not sure of your specific situation but it sounds like this might be an option.

Here is the link to a guide I wrote about installing Ubuntu from an ISO image on your hard drive.
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

---

### Post by streetlightman on 2011-05-12
thanks, im gonna give this a try in a little bit.  i'm currently installing it to the hard drive i want to use using a different computer.  i'm going to try to swap that hard drive out of the that computer and switch to the other computer and see what happens.  I know this doesn't work with windows but i've never tried it with linux.

---

### Post by drs305 on 2011-05-12
> **streetlightman said:**
> i'm going to try to swap that hard drive out of the that computer and switch to the other computer and see what happens.  I know this doesn't work with windows but i've never tried it with linux.

Linux doesn't have all the proprietary concerns that Windows does, so I don't think it's going to care if the drive doesn't match the original motherboard/hardware/etc setup.

Let us know if/how it works.

---

### Post by streetlightman on 2011-05-12
everything worked great.  thanks everyone!

---

