---
title: "stopped booting"
date: 2010-06-12
forum: General Help
---

### Post by petex on 2010-06-12
My ubuntu stoped booting
it might have to do with the fact that i tried to change parameters for powermizer however after removing powermizer from xorg.conf the issue still persist 


after booting the system seams to load but in the end sc reen like attached shows up and i can only use ctrl+alt+del to restart 

i think it is connected to  GPU/drivers/settings issue but i don't know what should i check

---

### Post by prodigy_ on 2010-06-12
Does Ctrl+Alt+F1 work?

---

### Post by petex on 2010-06-12
> **prodigy_ said:**
> Does Ctrl+Alt+F1 work?

unfortunatelly not
I should also mention i have same issue in recovery mode

I deleted my xorg.conf after removing powermizer line from it (first tried with removed line than deleted entire file - but keep in mind that the issue apeared before deleting ) did no good

(BTW i agree on many points you don't like ABOUT CURRENT LINUX for myself the biggest issue is stability of ubuntu (not to mention OO which constantly freezes my system))

---

### Post by wilee-nilee on 2010-06-12
If you boot to grub and hit e=edit and add nomodset to the kernel line then hold down the ctrl key and hit x it should get you back in to fix the graphic driver.

This nomodset is not kept with a reboot so you have to edit the driver.

If you get in or From a live cd run.
```
lspci | grep VGA
```
Post the output this will identify the card.

---

### Post by petex on 2010-06-13
nomodset does no good

lscpi from liveCD shows this

01:00.0 VGA compatible controller: nVidia Corporation Device 064c (rev a1)


(that's on 9,04 live CD as I could not find 10,04)

---

### Post by prodigy_ on 2010-06-13
> **petex said:**
> nVidia Corporation Device 064c (rev a1)
That's nVidia GeForce 9650M GT. AFAIK, 9.04 Live CD uses nv driver but 10.04 uses nouveau. Sounds like a possible nouveau driver bug. [Or an outdated BIOS](http://notepad.patheticcockroach.com/497/the-final-solution-to-nvidias-geforce-9650m-gt-drivers-problems/).

---

### Post by petex on 2010-06-13
> **petex said:**
> nomodset does no good

lscpi from liveCD shows this

01:00.0 VGA compatible controller: nVidia Corporation Device 064c (rev a1)


(that's on 9,04 live CD as I could not find 10,04)

not really i FIXED this poroblem  alreADy in 9.10 with bios update 
and 10.04 was working fine untill now (again i think my edit with powermizzer might have been the cause but I'm not sure if problem occured  after tweeking PM or a couple boots latter)

---

### Post by wilee-nilee on 2010-06-13
> **prodigy_ said:**
> That's nVidia GeForce 9650M GT. AFAIK, 9.04 Live CD uses nv driver but 10.04 uses nouveau. Sounds like a possible nouveau driver bug. [Or an outdated BIOS](http://notepad.patheticcockroach.com/497/the-final-solution-to-nvidias-geforce-9650m-gt-drivers-problems/).

Do you think the x-swat or fresh crack ppa's, might have the driver?

---

### Post by prodigy_ on 2010-06-13
> **wilee-nilee said:**
> Do you think the x-swat or fresh crack ppa's, might have the driver?

No clue. I don't use any nVidia cards right now. What is the real question is if 10.04 still installs the old nv driver along with nouveau. If yes, then it's possible to edit xorg.conf from Live CD and force nv driver.

I also recall some not so old controversy about nouveau where Linus himself complained that it doesn't always work and isn't actually ready to be included in production kernels.

---

### Post by petex on 2010-06-13
combination of removing splash vga line, 3 reboots,  and nomodset helped

thanks

---

### Post by sojiabolarin on 2010-10-19
Hi guys, I'm facing the same problem and I am very new on ubuntu. 
It all started after I installed the filezilla ftp client. How do I 
Get this fixed? Tnx

---

