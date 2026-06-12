---
title: "rebinstall grub"
date: 2009-12-16
forum: General Help
---

### Post by romanskier on 2009-12-16
I am trying to reinstall grub because it has errors. When trying to open a grub shell: "peter@peter-desktop:~$ sudo grub", I get this response: "[sudo] password for peter:",
and I cannot enter anything more. Thanks for the help.

---

### Post by jerrrys on 2009-12-16
just type in password; there will be no visual indication of this happening; then enter

---

### Post by Leppie on 2009-12-16
You can re-install grub with the following command:
```
$sudo grub-install /dev/sda ##substitute /dev/sda with the device you want grub to install to
```

this way you don't have to use the grub shell.

---

### Post by jerrrys on 2009-12-16
> **Leppie said:**
> You can re-install grub with the following command:
```
$sudo grub-install /dev/sda ##substitute /dev/sda with the device you want grub to install to
```this way you don't have to use the grub shell.

Leppie:

will that command allow me to move grub to another HDD?

edit...nevermind, im going to try it

---

### Post by Leppie on 2009-12-16
yes, like this you can install grub to whichever drive you prefer (i've seen posts of people installing grub onto 4 different drives, of course like this it becomes more difficult to determine off which drive grub is actually booting).

---

### Post by jerrrys on 2009-12-16
> **Leppie said:**
> yes, like this you can install grub to whichever drive you prefer (i've seen posts of people installing grub onto 4 different drives, of course like this it becomes more difficult to determine off which drive grub is actually booting).
 

tried grub on 4 HDDs and all it would do is cycle thur all HDDs to the last one.  have use live cd in the past to restore grub, but don't like it.  this looks like the ticket if it doesn't mess up my MBR

---

### Post by Leppie on 2009-12-16
> **jerrrys said:**
> tried grub on 4 HDDs and all it would do is cycle thur all HDDs to the last one.  have use live cd in the past to restore grub, but don't like it.  this looks like the ticket if it doesn't mess up my MBR

what are you exactly trying to accomplish (and repair)?

---

### Post by jerrrys on 2009-12-16
> **Leppie said:**
> what are you exactly trying to accomplish (and repair)?

nothing to repair, 6 drives running JBOD and changing things around all the time...got grub on #5 and want it on #3...

edit...also should say i have been meaning to try supergrub,but this is not a priority, just happen to come up...

---

### Post by Leppie on 2009-12-16
and you still have grub installed on several disks?

---

### Post by jerrrys on 2009-12-16
> **Leppie said:**
> and you still have grub installed on several disks?

no, just one

edit **AGAIN**...not that this should matter, but i did leave the first 512K on each drive open...

---

### Post by jerrrys on 2009-12-16
> **romanskier said:**
> I am trying to reinstall grub because it has errors. When trying to open a grub shell: "peter@peter-desktop:~$ sudo grub", I get this response: "[sudo] password for peter:",
and I cannot enter anything more. Thanks for the help.

its been 4 hours; have any luck?

---

