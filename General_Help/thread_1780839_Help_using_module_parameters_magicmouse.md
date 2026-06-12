---
title: "Help using module parameters magicmouse"
date: 2011-06-12
forum: General Help
---

### Post by willsomebody on 2011-06-12
Hello,

I have just gotten a magic mouse and the scroll speed is rather slow. After much googling, I have discovered that there is a way to do it in the kernel.

[http://kernel.ubuntu.com/git?p=abogani/ubuntu-natty-lowlatency.git;a=log;h=a63fcae229bfab4307e82a531861b7f311641630](http://kernel.ubuntu.com/git?p=abogani/ubuntu-natty-lowlatency.git;a=log;h=a63fcae229bfab4307e82a531861b7f311641630)

I do not, however have any idea how to do this. Can anyone point out to me how I might change the scroll_speed parameter? I tried ```
rmmod magicmouse
``` thinking that I could do something like ```
modprobe magigmouse scroll_speed=45
``` but rmmod magicmouse returned ```
ERROR: Module magicmouse does not exist in /proc/modules

```
It appears that magicmouse is not the name of the module that I need. I hope somebody can help with this. It is a bit frustrating to know that the option exists, but not how to change it.

---

### Post by willsomebody on 2011-06-12
Nevermind, I figured it out. It is a great mouse with ubuntu.

[http://blog.matws.net/post/2010/10/16/Correct-magic-mouse-scrolling-on-Linux](http://blog.matws.net/post/2010/10/16/Correct-magic-mouse-scrolling-on-Linux)

---

