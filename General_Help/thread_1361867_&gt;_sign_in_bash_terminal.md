---
title: "&gt; sign in bash terminal"
date: 2009-12-22
forum: General Help
---

### Post by bwgkennedy on 2009-12-22
Hello,

when using the bash terminal I typed in the following command:
[B]sudo mount -v --move /media/DAD'S IPOD /media/ipod
[/B]
I was hoping to move my mount point to another location, but the bash terminal prompt changed to a > sign and did not output a message.  I got out of this with Ctrl-c.  What does the > sign mean in bash?

---

### Post by audiomick on 2009-12-22
I think it means that bash is busy.

I am not sure if that move will work. I _think_ the name "DADS IPOD" comes out of the device itself, and if you want it to turn up as something else, you need to rename the device.

---

### Post by bwgkennedy on 2009-12-22
Thanks for the reply.

Yes, the name DAD'S IPOD does come from the device -- it's what I originally called it when I first used iTunes.  It was my understanding that the iPod would be mounted on /dev/sdb (I checked this with fdisk) and then automatically bound to /media/DAD's IPOD on connection of the device.  I was trying to see if I could move this to /media/ipod2 to see if rhythumbox would pick up the new mount point (/media/ipod2) when I started it.

---

### Post by rnerwein on 2009-12-22
oh folk - the only thing you have to do is to maskerate the " ' " in the command line. try  DAD\'SIPOD.
the ">" means that the bash is waiting for more input !
ciao
   richi

---

### Post by audiomick on 2009-12-22
> **rnerwein said:**
> oh folk - the only thing you have to do is to maskerate the " ' " in the command line. try  DAD\'SIPOD.
the ">" means that the bash is waiting for more input !
ciao
   richi

Oh yeah, forgot about that.:redface:
 Inverted commas mean "ignore what comes next", and spaces in names are a problem in the terminal as well.

The \ means "take the following literally as typed"

---

### Post by bwgkennedy on 2009-12-22
I tried typing in the \ character as you indicated but bash did not like it.  It spit out the usage rules for mount.  I also tried taking out the space from DAD'S IPOD as well (e.g. /media/DAD\'SIPOD ) but it said there was no device by that name.

---

