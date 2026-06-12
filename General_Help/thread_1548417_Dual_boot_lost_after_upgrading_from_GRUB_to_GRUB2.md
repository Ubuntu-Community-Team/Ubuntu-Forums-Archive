---
title: "Dual boot lost after upgrading from GRUB to GRUB2"
date: 2010-08-08
forum: General Help
---

### Post by jslandry on 2010-08-08
Hi, 

I am an absolute beginner at managing a Linux system, so please keep answer simple... 

I had Windows Vista and Ubuntu 9.04 installed and working nicely on the same laptop (dual boot). 

I decided to upgrade from GRUB to GRUB2 (before upgrading from Ubuntu 9.04 to 9.10, and then from 9.10 to 10.04), but I am no longer able to boot in Windows (I do not even see the option). 

Is there a way to fix this? 

Thanks!

---

### Post by oldfred on 2010-08-08
Welcome to the forum.

have you tried:
```

sudo update-grub
```

That almost always finds other operating systems.

---

### Post by jslandry on 2010-08-08
Hi, 

I have followed the instructions on the following site: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I think that "something" found Windows, but I could not have access to it after starting the computer. 

Any idea?

---

### Post by wilee-nilee on 2010-08-08
If you can post the bootscript in my signature, this will show a lot of pertinent information. Post it in code tags as described or by pasting txt to a reply highlight it then click on the # (code tags) in the reply panel.

---

