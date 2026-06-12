---
title: "Find my Ubuntu Version No."
date: 2010-09-12
forum: General Help
---

### Post by huzefa_from_kuwait on 2010-09-12
Hi guys, 

I am with a not-so-important question :)

I have been upgrading Ubuntu as its new distributions are released every six months regularly since quite some time now.

Is there a way I can find out which was the original installation version that I first installed after I formatted my disk.

I mean as far as I remember I have been using this state of my Ubuntu since 8.04 and have been upgrading since then, but I am not sure.

Any ways to find that out.

Thanks,

---

### Post by garyed on 2010-09-12
I don't know if this will work but its worth a try.
Make sure all your partitions are mounted & then do:
```
sudo find / -iname "vmlinuz*"
```

If your original kernel hasn't been deleted you can take the lowest number kernel & google it till you find what you're looking for. There's probably an easier way but that's all i know to do.

---

### Post by baddnady23 on 2010-09-12
Try using:

```
uname -a
```

---

### Post by huzefa_from_kuwait on 2010-09-13
vmlinux is 2.6.32-21 to 2.6.32-24

One thing is that I have grub1 with menu.lst so I suppose it could be pre 9.04 but I am not sure though.

Anyways its not a big deal, just out of curiosity.

---

### Post by plucky on 2010-09-13
Open **System > Administration > System Monitor > System Tab**

---

