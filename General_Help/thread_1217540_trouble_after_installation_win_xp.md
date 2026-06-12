---
title: "trouble after installation win xp"
date: 2009-07-19
forum: General Help
---

### Post by arturus on 2009-07-19
Hi.
i have problem with starting ubuntu. I tried install win xp but I didn't, because I didn't have a free primary partition. So i cancel install. So I had to restore grub. I did and now i have problem. When I start my ubuntu, i can read this
```
Log of fsck -C3 -R -A -a 
Sun Jul 19 17:37:03 2009

fsck 1.41.3 (12-Oct-2008)
data: clean, 62663/13107200 files, 33402108/52428127 blocks
fsck.ext3: Unable to resolve 'UUID=edfc2833-45d6-49fd-bd10-a72fe72b9ad2'

fsck died with exit status 8

Sun Jul 19 17:37:03 2009
----------------
```

What i should do now?

Thanks for advance
artur

---

### Post by merlinus on 2009-07-19
When you tried to install xp, perhaps it overwrote your linux installation.  In any event, it seems that the UUID for it changed.

Run from the live cd, open a terminal and enter

```
blkid
```

which will give the UUID for your linux partition.  Then you will have to compare that with what grub is listing. 

At the opening menu, press e, highlight the kernel line, and compare the two.  You can edit that line to the correct UUID by pressing e again, and then press b to boot.

If it works, you can then make the change permanent by editing /boot/grub/menu.lst.

---

### Post by arturus on 2009-07-19
never wrote something, when your girlfrind talk above you:) I forgot tell you, that after this massage, i press ctrl+d and ubuntu is running. 

Now, I think that problem can be linked with my automount disk?
But i will try yours way:)
thx

---

### Post by arturus on 2009-07-20
It was problem with automounting. Thx for halp

---

