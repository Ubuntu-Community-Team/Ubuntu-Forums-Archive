---
title: "how can i completely delete and reset everything?"
date: 2011-06-02
forum: General Help
---

### Post by nsk tacticzz on 2011-06-02
title says it all, plz help i need help

---

### Post by mike555 on 2011-06-02
Well , if you mean start over , then just use a Ubuntu cd to install Ubuntu to your hard drive .......
  in case you don't know how , download Ubuntu 10.04 , then burn it as an image onto a cd , then restart with the cd in your computer and click install .....

---

### Post by dozycat on 2011-06-02
and create again your partitions and format them.

---

### Post by silex89 on 2011-06-02
Format your computer...

Now, if you want a way to reset everything without incurring in installing the system again, I think there's a script (or several scripts) that allows you to do so, but I don't know it. IMO is always better a clean install

---

### Post by dozycat on 2011-06-02
and do it slowly.

---

### Post by nsk tacticzz on 2011-06-02
i want to delete everything and restart again without installing it, as im on a netbook without a disk drive.

---

### Post by Gremlinzzz on 2011-06-02
> **nsk tacticzz said:**
> i want to delete everything and restart again without installing it, as im on a netbook without a disk drive.

What is everything?system
you can install another system and remove the old one depending on what system you have.
on the left side you'll see playing around 
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Habitual on 2011-06-02
> **nsk tacticzz said:**
> without installing it, as im on a netbook without a disk drive.

open a terminal and type:```

rm ~/.config ~/.gconf

```

Logout and Login.

---

### Post by whatthefunk on 2011-06-03
Does your netbook have a USB drive?  If so you could do a fresh OS install from a live USB.

---

### Post by nsk tacticzz on 2011-06-03
> **Habitual said:**
> open a terminal and type:```

rm ~/.config ~/.gconf

```

Logout and Login.
it wont let me do this, says cannot remove is a directory.

> **whatthefunk said:**
> Does your netbook have a USB drive?  If so you could do a fresh OS install from a live USB.
 yh it has a usb but it wont boot off the usb. ad the programmes wont work. can u give me  LINK TO DOWNOAD ubuntu.

---

### Post by nsk tacticzz on 2011-06-03
> **Gremlinzzz said:**
> What is everything?system
you can install another system and remove the old one depending on what system you have.
on the left side you'll see playing around 
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

i want to completely get rid of anything and restart ubuntu 10.10 all over again.

---

### Post by whatthefunk on 2011-06-03
How did you get Ubuntu on it in the first place?

---

### Post by pqwoerituytrueiwoq on 2011-06-03
start slapping (repeadly) your F10 key as soon as you press the power button hopefully it will get you to a boot menu where you can select usb
if not change the boot order in the bios (F2 to get in there instead of F10)
unetbootin can make a bootable usb

---

### Post by nsk tacticzz on 2011-06-03
> **whatthefunk said:**
> How did you get Ubuntu on it in the first place?

via usb when there was no os on my netbook.

> **pqwoerituytrueiwoq said:**
> start slapping (repeadly) your F10 key as soon as you press the power button hopefully it will get you to a boot menu where you can select usb
if not change the boot order in the bios (F2 to get in there instead of F10)
unetbootin can make a bootable usb

where can i download a verioin of ubuntu thats works

---

### Post by HotForLinux on 2011-06-03
> **Habitual said:**
> open a terminal and type:```

rm ~/.config ~/.gconf

```Logout and Login.


I don't know if deleting only those configuration files will do what you want,  nsk tacticzz, but the correct command to delete those directories would be:

**$ rm -fr ~/.config ~/.gconf**[COLOR=Red][B]

BE VERY CAREFUL NOT TO LEAVE A SPACE BETWEEN THE "~", THE "/" AND THE "."[/B][/COLOR]

---

### Post by linuxinstalledfromhdd on 2011-06-03
> **nsk tacticzz said:**
> 



where can i download a verioin of ubuntu thats works

Try this one:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by whatthefunk on 2011-06-04
Google is your friend...  [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)

---

