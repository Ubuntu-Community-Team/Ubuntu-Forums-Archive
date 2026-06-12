---
title: "Help please !!!"
date: 2010-11-26
forum: General Help
---

### Post by aza148 on 2010-11-26
hi im helping my friend out they wanted me to install windows on there net book for them which was originally running ubuntu (gnome i think) i don't no much about linux my self on that t is a good system to use but i was putting windows xp on it as u do partioing the hard drive and its gone from a 160gb hard drive to 8gb and not finding any network adapters such as WLAN or ETHERNET PORT,
i dont understand this it doesn't normally go this wrong on any installation of windows and the net book is a dell mini 10 inspiron but when i put the service tag in the dell drivers search it pulls it up as a studio 1747 which is wrong.

has any one ever had a similar problem or does any one know what to do please if so help i would be really grateful my brain is fried 

thanks aza 148

---

### Post by Swagman on 2010-11-26
Well......

If the windows disk is a **Restore** disk then little can go wrong... But if it's an OEM or pirate version then you will need drivers for **EVERYTHING**... Including Motherboard drivers to enable Ethernet.

Vista/Win7 actually have a lot of these drivers in them but XP doesn't.

---

### Post by aza148 on 2010-11-26
it is an oem disk but when i try to install the drivers it wont let me but i just cant under stand how the hard drive has lost 152gb 

once the drivrs have installed the device still dosent show up it a complete puzzle.

---

### Post by sikander3786 on 2010-11-26
Delete all the partitions on that drive and see how much space is there. Windows might be listing the Linux partitions as "Unknown".

If you still can't figure that out, boot into an Ubuntu Live CD and post the output of following command from Applications > Accessories > Terminal.

```
sudo fdisk -l
```

It would tell us exactly about your partition setup. But remember, that was never a problem caused by Linux ;-)

Regarding drivers issue, that definitely needs to go to some Windows Forums.

---

