---
title: "new grub for dummies?"
date: 2010-04-28
forum: General Help
---

### Post by gcbzzzz on 2010-04-28
I considered myself pretty proficient in modifying grub in the past. menu.lst was as straightforward as it could be.

Maybe all we needed was a menu.lst with manual entries and a mere include with the automatic kernel list... but well, we ended up getting a sendmail configuration style.


can some good soul give me a simple dummie guide?

just the steps necessary to do the following i did on previous version:

1. edit /etc/grub/menu.lst
2. add custom options at the end
"title win safeboot
  rootnoverify (hd0,0)
  makeactive
  chainloader (hd0,5)/safeboot.mbr"
3. save.
4. boot
5. select newly created option.

what's the most straighforward way to get this same results with the new model? 

Thank you!

---

### Post by dino99 on 2010-04-28
> **gcbzzzz said:**
> I considered myself pretty proficient in modifying grub in the past. menu.lst was as straightforward as it could be.

Maybe all we needed was a menu.lst with manual entries and a mere include with the automatic kernel list... but well, we ended up getting a sendmail configuration style.


can some good soul give me a simple dummie guide?

just the steps necessary to do the following i did on previous version:

1. edit /etc/grub/menu.lst
2. add custom options at the end
"title win safeboot
  rootnoverify (hd0,0)
  makeactive
  chainloader (hd0,5)/safeboot.mbr"
3. save.
4. boot
5. select newly created option.

what's the most straighforward way to get this same results with the new model? 

Thank you!

follow my signature

---

### Post by gcbzzzz on 2010-04-28
> **dino99 said:**
> follow my signature

ok, if i understood the section "adding entries" (which also covers how to remove entries..:)

1. edit /etc/grub.d/19_win_safeboot
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
menuentry "win safeboot" {
rootnoverify (hd0,0)
makeactive
chainloader (hd0,5)/safeboot.mbr
}
```
2. sudo chmod +x !$
3. sudo update-grub || grub-update (which one)?
4. boot
5. select newly created option.

---

### Post by dino99 on 2010-04-28
why would you want to tweak everything ? keep it simple :)

sudo grub-mkconfig && update-grub

---

### Post by gcbzzzz on 2010-04-28
hum.. no luck

my changes didn't appeared there.

added the echo "adding $0" trick. and i never see that message after update-grub

Update: ok, missed your last message. So step 3 is:
3. sudo grub-mkconfig && sudo update-grub

thanks!

---

