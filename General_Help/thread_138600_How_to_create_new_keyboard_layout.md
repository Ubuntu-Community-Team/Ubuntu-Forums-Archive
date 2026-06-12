---
title: "How to create new keyboard layout?"
date: 2006-03-02
forum: General Help
---

### Post by filosof on 2006-03-02
Is it possible to create new, or customize existing keyboard layout in Ubuntu 5.10 Gnome? Just wanted to rearrange some buttons in Russian Phonetic keyboard layout to match Russian Student... Or, is it possible to get new layouts from somewhere and install them?..

Thanks for answers! :)

---

### Post by DonVla on 2006-03-02
hello,

you have to install ```
xkbutils
``` and then enter > setxkbmap ru for the russian layout.

vlad

---

### Post by filosof on 2006-03-02
Thanks! But it is not exactly the case.. 'setxkbmap ru' changed keyboard layout; when I was wondering, is it possible to create own layout (based on the some existing one)?

---

### Post by tbg58 on 2006-03-02
I'd also like these instructions to aid my transition from Windows to Linux.  I understand how to load the Russian locale-- I'm an American and a native English speaker, and more to the point, I touch type in English.  I used a utility provided by the OS vendor to create a keyboard layout so I could type in Cyrillic using a phonetic equivalent keyboard, and I am quite sure that Gnu/Linux will have a tool for the same purpose.  I want to type Russian, but I don't want to have to use the Russian native keyboard layout; I want to use a keyboard layout like the AATSEEL (American Association of Teachers of Slavic and Eastern European Languages) student layout.

Thanks for any assistance, and thanks also to the author of the original post.

Kindest regards,

Rob in TN

---

### Post by tbg58 on 2006-03-02
I'll Google around tonight and try to post my results -- xkbutils looks like it will do the job with a bit of finagling...
Later,
Rob

---

### Post by filosof on 2006-03-04
I found the solution. All interesting stuff is stored in /usr/X11R6/lib/X11/xkb folder. There are all installed keyboard maps. You can edit them, and X will pick up it from there.

One interesting link:
[http://www.charvolant.org/~doug/xkb/html/node1.html](http://www.charvolant.org/~doug/xkb/html/node1.html)

---

