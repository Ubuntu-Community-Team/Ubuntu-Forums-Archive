---
title: "Boot to USB with new grub boot default?"
date: 2010-10-19
forum: General Help
---

### Post by JohnnyLongarms on 2010-10-19
Tried to keep the title short, but informative. I wonder if that worked..

Any way, I have a dual boot box (Ubuntu 10.04 / Windows 7) and want to go headless. Here's my plan (Don't know if this is possible, but it's Linux.. anything is possible!)

I set GRUB to boot to windows by default.

I create a USB drive that has a separate GRUB or just a separate "grub" file that has ubuntu set as the default. 

Now I can boot the computer without the usb, and VNC into windoes. Or I can boot the computer with the usb in and VNC into Ubuntu. 

Or any other ideas? I just need to be able to choos ewhich OS I boot to, but do it without a head.

Thank you!!

---

### Post by VMC on 2010-10-19
You can install grub onto your usb device and if you BIOS allows, switch on boot up either way. If that's what your asking. I have a usb device with grub installed and can boot up either my internal hard drive or the usb partition.

---

### Post by JohnnyLongarms on 2010-10-21
Yeah, that sounds like the plan. Good to hear people use it. I figured I would set my boot priority to USB>HD , and I'll be all set.  
 
Problem is I can't figure out how to install GRUB onto a USB drive. More searching I guess. It's hard 'cause I'm a total linux noob, and many of the 'simple' guides require a bit of prior knowledge. 
 
Thanks for the reply!
 
--edit-- I forgot what my original question even was haha. So once I can do that, will the GRUb that's installed on the USB drive have a different file that tells which OS to dedault to? (Used to be menu.lst or grub.conf, now it's grub something or other) so that when the USB is inserted it boots to a different OS than when it's not inserted?

---

