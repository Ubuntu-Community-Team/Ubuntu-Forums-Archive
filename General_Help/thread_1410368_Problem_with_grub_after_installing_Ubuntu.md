---
title: "Problem with grub after installing Ubuntu"
date: 2010-02-18
forum: General Help
---

### Post by bushtangu on 2010-02-18
i have xp in my destkop, after installing ubuntu 9.10 grub doesnt show. i have try a lot of thing but nothing changed. any help please. thank you

---

### Post by Crafty Kisses on 2010-02-18
> **bushtangu said:**
> i have xp in my destkop, after installing ubuntu 9.10 grub doesnt show. i have try a lot of thing but nothing changed. any help please. thank you

Now I'm not sure what you're asking. I'm assuming the question is you have installed Ubuntu, now XP is not showing on your GRUB menu list? Please tell me if this is correct, then I can help you a bit further.

---

### Post by bushtangu on 2010-02-18
thank you for your reply. i have the problem that grub isnt showing. my pc is directly booting to xp

---

### Post by Crafty Kisses on 2010-02-18
Hmm, sounds like GRUB must have been installed on your root partition. I would suggest getting the Ubuntu LiveCD and try and see where GRUB is at, so if you can get back into Linux via the LiveCD, and see your partition table, so run:
```
fdisk -l
```
Then look at the partition table, and see your Linux partition, and try mounting it:
```
mount /dev/sd?? /mnt
```
Then either reinstall GRUB, or see where GRUB is installed at, you can always use the following command:
```
find /boot/grub/stage1
```
Then from there you can point GRUB to your MBR. Hope this helps.

---

