---
title: "Triple Boot"
date: 2011-04-08
forum: General Help
---

### Post by Andrenap on 2011-04-08
Kinda weird question. I'm in my friends PC and he asked me to install Ubuntu (i had the cd with me and convinced him actually). Install successful. But now is the important part. e first had a Mac, then installed a Windows, and now Ubuntu, but Mac is kinda bugged and he wants to remove it. How do I remove Mac, without affecting Windows or Ubuntu? It's in a separated partition, so can I just format it and remove it from the boot list?

---

### Post by earthpigg on 2011-04-08
is it Apple hardware, or standard x86 hardware (the type of hardware commonly called a "PC" on the "PC versus Mac" commercials)?

if it is x86 hardware, and grub is the bootloader, then yes: adjust grub and remove or repurpose the OS X partition.

---

### Post by Andrenap on 2011-04-08
The PC came with Windows, so I can just wipe Macs partition. That's what you're asking right? -Just to be safe, it's not my PC after all

---

### Post by earthpigg on 2011-04-09
assuming you haven't installed the OS X bootloader onto the MBR or anything similarly crazy,

yup, wipe away.

---

