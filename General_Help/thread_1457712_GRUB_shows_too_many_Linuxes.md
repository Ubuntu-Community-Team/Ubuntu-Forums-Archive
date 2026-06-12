---
title: "GRUB shows too many Linuxes"
date: 2010-04-19
forum: General Help
---

### Post by altjx on 2010-04-19
I'm using Ubuntu 10.4 Beta 2 and for some reason, GRUB shows this menu
[IMG]http://img101.imageshack.us/img101/1509/dsc00630xe.jpg[/IMG]

---

### Post by altjx on 2010-04-19
omg im sorry its so huge, idk how to shrink it.
there

---

### Post by polardude1983 on 2010-04-19
> **altjx said:**
> omg im sorry its so huge, idk how to shrink it.
there

Omg so does mine. Thats the next thing i need to fix

---

### Post by altjx on 2010-04-19
> **polardude1983 said:**
> Omg so does mine. Thats the next thing i need to fix

Yeah, lol. Not sure why it does that. I'm thinking it's still showing 9.10, 10.4 Beta 1, and 10.4 beta 2

---

### Post by arrimapirate on 2010-04-19
Go to Synaptic then search for and uninstall all the kernel versions EXCEPT 2.6.32-21. This will get rid of all the old kernels.

---

### Post by altjx on 2010-04-19
> **arrimapirate said:**
> Go to Synaptic then search for and uninstall all the kernel versions EXCEPT 2.6.32-21. This will get rid of all the old kernels.

Thanks :]

---

### Post by arrimapirate on 2010-04-19
Yep no problem. Need to know how to get rid of the memtest86+ ones too?

---

### Post by altjx on 2010-04-19
> **arrimapirate said:**
> Yep no problem. Need to know how to get rid of the memtest86+ ones too?

Yeah, that'd be cool. Are they even worth keeping?

---

### Post by altjx on 2010-04-19
Just got rid of memtest too. Thanks again man :]

---

### Post by arrimapirate on 2010-04-19
Run "sudo chmod -x /etc/grub.d/20_memtest86" then "sudo update-grub" without quotes
This will stop the memtest option from being loaded onto grub by making it non-executable then generating a new grub.conf file.  

Its up to you if they ware worth keeping. They are used to test your ram, but i have never used them and took them off.

Always glad to help

---

### Post by lavinog on 2010-04-19
> **altjx said:**
> Yeah, lol. Not sure why it does that. I'm thinking it's still showing 9.10, 10.4 Beta 1, and 10.4 beta 2

Those are all lucid kernels...since lucid is in beta, it goes through many updates...including kernels.

At some point the computer janitor used to offer a way to clean unused kernels, but there were some problems with it.  I don't know if it was decided to add that back to it.

memtest can come in handy if you ever have stability issues...it doesn't take up much space, but removing it is not that big of a deal since you can run it from the live cd.

---

### Post by Dell Inspiron 1501 on 2010-04-19
Ubuntu tweak offers an easy gui to remove extra kernels, among other things; it's pretty useful.   [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

