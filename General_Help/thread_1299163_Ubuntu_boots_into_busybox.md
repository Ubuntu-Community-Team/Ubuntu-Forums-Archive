---
title: "Ubuntu boots into busybox"
date: 2009-10-23
forum: General Help
---

### Post by SkaKid on 2009-10-23
hey ive been useing linux for about a year now. i would not codsider myself a complete noob but certainly no expert. but any way my ubuntu computer (dell latitude xt) which is running jaunty has been working fine... until i got booted into a place ive never been before. its like a terminal but it says busybox and when i type commands in it says "initramfs" i have attached photos of my screen but i warn you they arnt the best of quality. but to the point if anybody has any idea of what i should do to fix this please tell me, and i also want to save all my music and videos.


thanks,
Henry

---

### Post by jalm111 on 2009-11-06
I have this exact same problem trying to boot into the new kernel. Anyone?

---

### Post by diskotek on 2009-11-07
i have the same problem while i'm booting from a flashdrive (with 9.04), i can not install ubuntu nor use it live.

---

### Post by sugobsugob on 2009-11-08
Hi,

I got a similar situation [boots into BusyBox about 30secs after selecting first option that begins 'Try Ubuntu' from the initial boot menu] when I recently created a ubuntu 9.10 boot optical disc from torrent downloaded iso - booting from a 9.04 disc had previously worked fine [i.e. booted a Live Ubuntu system] on exactly the same hardware. Both were Ubuntu amd64 bit desktop versions burned to a DVD-RW disc.
I could get the 9.10 to boot from disc by selecting key F6 'Other Options' on the initial boot screen and changing the top option [acpi=off] to selected [puts a little x to the left of it], clicking escape key [to get rid of the options menu] then run the 'Try Ubuntu' option.
I'd probably try some of the other options if this hadn't worked...

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I have not tried using this 9.10 disc to do a fresh install [rather than running live]. Originally installed Ubuntu 9.04 onto my new system a few months ago and recently upgraded to 9.10 by download - all no issues

My hardware is is all pretty newish
Chipset: Intel SX58  [Shuttle SX58H7]
Optical Disc: LG CH08LS10 [SATA]
Hard Disc: Corsair P128 SSD [SATA]

HTH

M

---

### Post by Druke on 2009-11-08
Usually this is the result of a bad upgrade function. 

For flashdrives and cds, check the image file to verify it works (md5s are good, if you dn't know how to do that, try running it through virtual box to see if it boots up), then try re copying the files to your medium.


If this is happening on a long time stable install, I'm sorry to say i have no idea how to help you, though I bet there are people around that do.

---

