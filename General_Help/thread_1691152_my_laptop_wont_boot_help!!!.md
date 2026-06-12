---
title: "my laptop wont boot? help!!!"
date: 2011-02-19
forum: General Help
---

### Post by amna543 on 2011-02-19
so when i turn my laptop on the screen goes black and says....
 
primary hard diskdrive 0 not found
 
no bootable devices available--strike F1 to retry boot, F2 for setup utility
 
btw i have a dell inspiron 510m
 
if anyone could help i would be very greatful!:confused:
amna

---

### Post by TeoBigusGeekus on 2011-02-19
Hd failing or a bad connection.
Has the laptop sustained any physical damage lately?

---

### Post by amna543 on 2011-02-19
i did drop my laptop but that was absolutly ages ago!
thanx for ansering!

---

### Post by elfuego on 2011-02-19
Could be anything, but smells like a dead (or a disconnected) hard drive to me. Go to BIOS of your laptop and see if the HDD gets detected at all. If so, then insert the Ubuntu LiveCD, boot from it and try to access your hard drive. Then, let us know of the result :)

If your HDD doesnt get detected by BIOS at all, then either send the laptop to a certified dealer for repairs (HDD failure), or take the matter in your hands, open the laptop and check if the HDD is connected (wired) correctly. If so, then your HDD is dead and the next step is to buy&install a new one :(

---

### Post by TeoBigusGeekus on 2011-02-19
Your problem seems to be a hardware one.
Boot up with an ubuntu live cd/usb and post us the output of 
```
sudo fdisk -l
```
(-L), so that we can see whether your hd is accessible.

---

### Post by amna543 on 2011-02-19
but it wont let me acsess anything ive tryed evreything but it wont do anything??

---

### Post by elfuego on 2011-02-19
> **amna543 said:**
> but it wont let me acsess anything ive tryed evreything but it wont do anything??

It must let you access your BIOS (I guess by pressing F2 or F10 or F12 while booting). See if it gets detected there.

Please be more specific when stating 'tried everything'.

---

### Post by TeoBigusGeekus on 2011-02-19
Go into your BIOS and select cd as your primary boot device.
Insert the ubuntu cd then select "Try ubuntu without change to my pc".
See if you can see your hd from the live session.

---

