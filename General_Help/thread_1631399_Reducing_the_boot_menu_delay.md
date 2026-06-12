---
title: "Reducing the boot menu delay?"
date: 2010-11-26
forum: General Help
---

### Post by germanix on 2010-11-26
In Ubuntu 8.04, when I wanted to reduce the boot menu delay I had to do the following:
enter in terminal: gksu gedit /boot/grub/menu.lst
I then looked for the line that begins with timeout and changed the value (shortened the delay)
Now with ubuntu 10.10, when I tried this I do get into the Gedit text editor as with 8.04 but it is completely blank, no entries at all? So nothing to change! So how do I change the boot menu delay in ubuntu 10.10? 
Appreciate any help.

---

### Post by sikander3786 on 2010-11-26
It has changed a bit in Grub2.

You need to edit this one.

```
gksudo gedit /etc/default/grub
```

In that file, this is what you are looking for.

```
GRUB_TIMEOUT=10
```

And that would not work unless this line is commented as here.

```
#GRUB_HIDDEN_TIMEOUT=0
```

And at last, you need to update Grub by,

```
sudo update-grub
```

Or the changes would not take effect.

More info here.

[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29](https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29)

Good Luck!

---

### Post by drs305 on 2010-11-26
Grub 2 is very much different, including a different file structure. For an introduction and probably more than you need to know, look at the "G2-Basics" link in my signature line. For just changing the timeout, check the much simpler "G2-Tasks" link.

---

### Post by germanix on 2010-11-26
You guys are just brilliant. Worked like a charm. Thank you a lot for your help and your quick response. Have a nice day.

---

