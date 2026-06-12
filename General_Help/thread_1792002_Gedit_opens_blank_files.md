---
title: "Gedit opens blank files"
date: 2011-06-27
forum: General Help
---

### Post by nysnsweet on 2011-06-27
hello,

I have been trying to customize my Ubuntu 10.04 software and dual boot configurations, and all commands that require me to use sudo gedit in terminal all open up gedit but the document is blank.

Can anyone help me figure out why all gedit files are blank and help me resolve this issue?

Thanks

---

### Post by bodhi.zazen on 2011-06-27
Blank documents are typically due to either ;

1. The document does not exist, and you must write it.

2. Wrong path or a typo.

Post an example and we can check your syntax.

Also with graphical applications, such as gedit, best to use gksu

```
gksu gedit
```

---

### Post by nysnsweet on 2011-06-27
> **bodhi.zazen said:**
> Blank documents are typically due to either ;

1. The document does not exist, and you must write it.

2. Wrong path or a typo.

Post an example and we can check your syntax.

Also with graphical applications, such as gedit, best to use gksu

```
gksu gedit
```

This is what I've been trying to access:
sudo gedit /boot/grub/menu.lst
sudo gedit /etc/grub.d20_memtest86+

---

### Post by nothingspecial on 2011-06-27
> **nysnsweet said:**
> This is what I've been trying to access:
sudo gedit /boot/grub/menu.lst
sudo gedit /etc/grub.d20_memtest86+

You are following old instructions that no longer apply.

What are you actually trying to do?

---

### Post by bodhi.zazen on 2011-06-27
> **nysnsweet said:**
> This is what I've been trying to access:
sudo gedit /boot/grub/menu.lst
sudo gedit /etc/grub.d20_memtest86+

Ubuntu uses grub 2 , so there is no /boot/grub/menu.lst

The second is an obvious typo, you left a / out of the path.

---

### Post by coffeecat on 2011-06-27
> **nysnsweet said:**
> This is what I've been trying to access:
sudo gedit /boot/grub/menu.lst

Unless you upgraded your 10.04 system from 9.04 or earlier, you will not have a menu.lst file. The menu.lst file is a legacy grub file - Ubuntu 10.04 comes with grub 2.

> **nysnsweet said:**
> sudo gedit /etc/grub.d20_memtest86+

That is a grub2 file, but there's a typo in the path in your command. If you made the same typo in the terminal, that would explain the blank gedit window.

It's /etc/grub.d/20_memtest86+, not /etc/grub.d20_memtest86+

---

### Post by nysnsweet on 2011-06-27
Thank you coffeecat and bodhi.zazen.  You are both right and I got it to work.  Haha I panicked over nothing.  Thanks again!

---

