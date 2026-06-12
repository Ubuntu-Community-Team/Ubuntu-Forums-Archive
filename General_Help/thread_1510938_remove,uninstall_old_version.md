---
title: "remove,uninstall old version"
date: 2010-06-16
forum: General Help
---

### Post by keviano on 2010-06-16
hi im just getting confused/frustrated about ubuntu,as far as i can tell im using 8.04(hardy heron) what is most frustrating is when grub loads im getting diff vers. 2.6.24.25,  2.6.24.26  2.6.24.27,  i sorta understand version updates. ?! how do i delete old versions from grub.(i think ive done it before with pkt mangr but i dont seem to be able to find/search this anymore,its not a real prob just gets fruts that grub loads with diff vers,please note i dont want to upgrade  to zany zebra::lolflag: :guitar:

---

### Post by TeoBigusGeekus on 2010-06-16
[http://ubuntuforums.org/showthread.php?t=1502173]("http://ubuntuforums.org/showthread.php?t=1502173")

---

### Post by elliotn on 2010-06-16
Have the same problem also, I have 2 kernels in my grub menu

---

### Post by keviano on 2010-06-16
look im happy with what ive got, i just want to remove at least 1 version(at least i will have 1 ? backup

---

### Post by robert shearer on 2010-06-16
Yes, it is safer to have at least two kernels, the most current that you are using and its predecessor as a spare to boot into if you mess-up  the first and need to fix it.

To remove others look in synaptic for 

```
linux-image
```

and find the one/s you want to remove.
 Right click and select for removal and apply.(other packages relating to that image will be removed too.)
 Don't remove linux-generic.

Grub should be updated and next reboot those kernels will not be shown.

---

