---
title: "Grub loading... error 18"
date: 2009-07-12
forum: General Help
---

### Post by larscapaldi on 2009-07-12
Ok first of all i've searched all the existing threads but none seemed to offer me a solution. When trying to boot ubuntu it gives me the above lines. I've tried messing around with the bBIOS settings but nothing seemed to offer  a solution. Am now booting with a mandriva live cd i still had somewhere around, and this whole story is really frustrating me. From what i read it would be the kernel that is not within reach because of the hdd being to large but as i can't boot ubuntu i cannot change these settings...any help would be greatly appriciated

cheers

Lars

---

### Post by northern lights on 2009-07-12
With the internal disk(s) / partiton(s) mounted, run```
update-grub
``` from your Mandriva Live-CD (or any other, for that matter). Reboot. Does the error persist?

---

