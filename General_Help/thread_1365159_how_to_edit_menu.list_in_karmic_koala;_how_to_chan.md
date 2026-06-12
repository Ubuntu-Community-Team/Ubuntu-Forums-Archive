---
title: "how to edit menu.list in karmic koala; how to change the order of OS in grub?"
date: 2009-12-26
forum: General Help
---

### Post by emigrant on 2009-12-26
hi all,
how to edit menu.list in karmic koala. i cant find the file.
the purpose is i want to edit the order of the operating systems in grup.
i want to bring xp to the top (dual booting)

thank you very much.

---

### Post by audiomick on 2009-12-26
Hi.
Karmic 9.10 has switched to Grub2, which doesn't use menu.list anymore.
Instructions here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by emigrant on 2009-12-26
thanks for the info.
but how can i bring xp to top?
thank you.

---

### Post by Mahngiel on 2009-12-26
rearrange /etc/grub.d/40_custom

the link audiomick sent you will answer all

---

### Post by emigrant on 2009-12-26
this grub2 is a real mess.
i don't know how to edit the boot order. why they changed the simple way of old grub?

---

### Post by Mahngiel on 2009-12-26
it's actually rather neat, imo.  The script is compiled from many other "departments" and made into one big "store". you can, per se, change the men's clothing aisle, but keep the groceries.

ya pickin up what i'm layin down?

---

### Post by rmjohnson144 on 2009-12-28
I just wanted to let you know I finally figured this out sedarching the forums for a few hours and here was the simplest solution I found so far.

> **fooman said:**
> you could always use "startupmanager"...it is available in synaptic, or in a terminal:

```
sudo apt-get install startupmanager
```

after it installs,  find it in system > administration > startup-manager

look under the boot options tab > default operating system

hope that helps

Luck
-=Mark=-

---

### Post by emigrant on 2009-12-28
yes. thanks for everybodys input. appreciate very much :)

---

