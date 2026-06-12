---
title: "strange booting problem"
date: 2010-08-03
forum: General Help
---

### Post by tanyeun on 2010-08-03
hi guys,

since I upgraded to Lucid Lynx
it seems that every 30 times or something boots
the computer will automatically force me to do hardware check
while booting
it's very inconvenience sometimes bcs 
sometimes u boot the computer and u need it right away
is there any other way to choose it to do the hardware check later??

and the screen always show something similar to the attached
any ideas??

thx,

David

---

### Post by mendhak on 2010-08-03
Hi, I believe this thread should be very similar to yours:

[http://ubuntuforums.org/showthread.php?t=1496878](http://ubuntuforums.org/showthread.php?t=1496878)

Hopefully it helps in some way.

---

### Post by tanyeun on 2010-09-11
thx mendhak :)
these link really useful
but I finally find out my problem is about forced disc check
after 30 boots by defaults

after a long searching for answers
I figured the best way to resolve this issue 
is to install AutoFsck
which will move the forced disc check to shutoff

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)  

and you can use this command to check how many times you have
booted so far
$ sudo dumpe2fs -h /dev/sda1 | grep -i 'mount count'

---

