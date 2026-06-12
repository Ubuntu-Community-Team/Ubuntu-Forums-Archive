---
title: "Installing on RAID"
date: 2006-02-28
forum: General Help
---

### Post by SleightfulMind on 2006-02-28
I am about to get 9 hard drives for my new machine. I was going to arrange them such that 8 belong to a RAID 50 (two RAID 5 each with a hot spare striped together) and the remaining hard drive would be my boot device. Could someone explain what steps I need to take to acheive this arrangement? Can this be done through the Ubuntu installation program?

Thanks!

---

### Post by KnottyMan on 2006-02-28
I would just install Ubuntu on the single first, get the OS all happy, then you just need to use the md tools to slap them all together.  You can do it all in the install, but might be easier after the fact.  Never tried 50 with md, but you should be able to I guess.

What controller are you going to run all these with?

---

### Post by Shay Stephens on 2006-02-28
Horrible n00b question here but what is md tool?  And can ubuntu do software raid or do you have to use a hardware controller?

---

### Post by KnottyMan on 2006-02-28
md = multiple disk

It's Linux's software raid package.  mdadm --help or man mdadm.

You could raid usb floppy drives together if you had enough USB ports/drives.

---

### Post by Shay Stephens on 2006-02-28
Many thanks :-)

---

