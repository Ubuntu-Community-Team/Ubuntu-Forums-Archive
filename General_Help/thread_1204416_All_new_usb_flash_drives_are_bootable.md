---
title: "All new usb flash drives are bootable?"
date: 2009-07-04
forum: General Help
---

### Post by stozi on 2009-07-04
I read that all usb flash drives made after a certain recent year incorporate a standardized specification that includes bootability. 

Can anyone confirm/deny this? Can I just buy a new flash stick instead of a new optical drive?

Thanks!

---

### Post by FrogPrince on 2009-07-04
The issue isn't so much if the usb drive is bootable as can your computer be booted off a usb device? Most modern computers can, but the older ones can't. And amongst the newer computers, some won't boot off a simple USB stick without an external power supply. Also, you can make any stick bootable no sweat - just use a tool like Gparted or cfdisk.

---

### Post by tgalati4 on 2009-07-04
And you can make just about any computer with USB to boot from USB using a boot floppy or boot CD that has the appropriate boot image.  There are a few floating around that a simple search will bring up.  Super Grub Boot Floppy comes to mind.

---

### Post by stozi on 2009-07-04
Ok thanks, my computer does have an FDD boot option in bios. 

I thought drives had to have a boot sector designed into them or something. Mine hasn't wanted to work with slax or instructions form pendrivelinux.com, but I'll give gparted a shot.

---

### Post by x33a on 2009-07-05
try unetbootin.

---

### Post by philcamlin on 2009-07-05
> **x33a said:**
> try unetbootin.

unetbootin is reallygood for usb's 

i recommened it too

---

### Post by Ocxic on 2009-07-05
Careful, there are USB sticks that offer encryption or extra security. 
I ran into one of these and it had an extra partition about 25 MB in size for the software that it used for the security features. 
I ended up returning it for another one with such a feature as it would not let me boot to it at all since the security partition was a hidden primary.

---

### Post by lisati on 2009-07-05
> **stozi said:**
> Ok thanks, my computer does have an FDD boot option in bios. 
I might be mistaken, but I think "FDD" is "floppy disk drive"..... my laptop has both FDD and USB in its boot menu.

---

### Post by stozi on 2009-07-05
Thanks for the headsup on unetbootin! It brings tears to my eyes.

Oh yeah, Floppies... forgot about those... thanks too.

If my flash drive has one partition, do I need to make sure it's primary or anything like that?

Fantastic, the way this is going opticals are history for me!

---

