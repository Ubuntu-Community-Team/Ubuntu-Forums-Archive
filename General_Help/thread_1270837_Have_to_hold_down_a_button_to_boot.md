---
title: "Have to hold down a button to boot"
date: 2009-09-20
forum: General Help
---

### Post by ColdZer0 on 2009-09-20
I have a hp pavilion dv6527ea and Im running 8.10
Ever since I installed ubuntu I have to hold down a button on my keyboard to make the loading bar progress and if I don't it will just sit there until I do so.
Is there anyway to fix this? I've tried reinstalling an it doesnt help.
Any help would be great.

---

### Post by SlugSlug on 2009-09-20
you could look at (I think its) CTRL + ALT + F8  to see whats going on --  or remove 'quiet splash'   from /boot/grub/menu.list  and you'll see stuff loading and where it stops

---

### Post by ColdZer0 on 2009-09-20
When I did this it stops after every line of code

---

### Post by SlugSlug on 2009-09-20
sounds like this...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247)

---

### Post by ColdZer0 on 2009-09-20
How do i boot in nolapic?
This seemed to work with most people but I have no idea how to

---

### Post by SlugSlug on 2009-09-20
[http://ubuntuforums.org/archive/index.php/t-148761.html](http://ubuntuforums.org/archive/index.php/t-148761.html)

---

### Post by ColdZer0 on 2009-09-20
Thanks so much, it worked :D

---

### Post by SlugSlug on 2009-09-20
cool

---

