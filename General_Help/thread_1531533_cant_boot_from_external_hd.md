---
title: "cant boot from external hd"
date: 2010-07-15
forum: General Help
---

### Post by Honz@ on 2010-07-15
I installed Ubuntu 10.04 on my external HD from USB flash drive. But if i want to boot it, only black screen with blinking _ appears. Im total noob so maybe i made a mistake in installation, so here is how i did it (if i remeber correctly):
unplugged internal hd (i have vista on it and i didnt want to risk damaging it)
booted from live USB
plugged external hd
clicked installation
it asked me if i want to unmount it, becouse otherwise i would be able to edit partitions, so i clicked yes.
when it asked me where to install ubuntu i clicked something like "make partitions manually"
i made /, swap and home partitions
started instalation, whe finished it asked me if i want to reboot or continue trying ubuntu, i clicked continue
i switched off pc and plugged internal HD
booted to vista, worked
restart, changed booting priority of external HD, booted from it, black screen with _ appeared.

next day i tryed to boot from live USB like before, black screen appeard with text:

error: no such device (and many numbers)
grub rescue>

any idea what i messed up? And is it possible to fix it without risking damage to vista?

---

### Post by Braik on 2010-07-15
Hi,
 
Yes, you made mistakes in installation, first mistake: unplug internal HD.
 
GRUB needs the mapping and location of all drives to know how to boot.
 
I have never tried to install Ubuntu on an external drive but I think that you should treat it as a normal drive, and install again without unpluggin the internal.
 
What I don't know is if you do like the MBR (Master Boot Record) of your vista will be or not erased. This could make you panic but you should not since this can be fixed (lot of helps and forums on how to do that). If the install don't touch your MBR then you should be able to run both even without unpluggin your external drive.

---

### Post by Honz@ on 2010-07-15
> **Braik said:**
> Hi,
 
Yes, you made mistakes in installation, first mistake: unplug internal HD.
 
GRUB needs the mapping and location of all drives to know how to boot.
 
I have never tried to install Ubuntu on an external drive but I think that you should treat it as a normal drive, and install again without unpluggin the internal.
 
What I don't know is if you do like the MBR (Master Boot Record) of your vista will be or not erased. This could make you panic but you should not since this can be fixed (lot of helps and forums on how to do that). If the install don't touch your MBR then you should be able to run both even without unpluggin your external drive.
I read multiple instruction how to install ubuntu on external HD and at least two of them stated that its safer to unplug internal HD before installation. And isnt there a way to make sure Ubuntu wont earse my MBR?

and also, if Grub needs to know location of all drives to know how to boot, does it mean i wont be able to boot on other computers?

---

### Post by Braik on 2010-07-15
Can you give me the instructions that you read at? Curious about the way they do it.

---

### Post by Honz@ on 2010-07-15
> **Braik said:**
> Can you give me the instructions that you read at? Curious about the way they do it.
[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)
"***[COLOR=#FF0000]IMPORTANT[/COLOR]:**  Ensure that all internal hard drives are disconnected from your computer  during the install (pull your SATA or IDE cables)*"

---

