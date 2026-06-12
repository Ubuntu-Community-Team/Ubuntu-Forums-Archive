---
title: "Hardening Ubuntu 11.10"
date: 2011-10-15
forum: General Help
---

### Post by dusanyu on 2011-10-15
little note I tend to Psychotic about system security and I find these two things to rub me the wrong way

problem 1 Guest account i don't want this how do I make it **_gone_**. (this was a poor choice by the Ubuntu devs. to have this on by defalcate. 

two "Me menu" indicator fast user switching is another hole I want plugged is there away to disable this as well?

---

### Post by dusanyu on 2011-10-16
And I found the fix thanks to the documentation for Light DM 

to remove the guest account login from do the following 

open the file /etc/lightdm/lightdm.conf with your favorite text editor

than simply add the line ```
allow-guest=false
``` to the end of the file so it reads like this 

```
[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
allow-guest=false
```

changing this  removed the "fast user switching" indicator for me 
[IMG]http://i12.photobucket.com/albums/a216/Dusanyu/Screenshotat2011-10-16172548.png[/IMG]

it is takeing bit of work but 11.10 could turn out to be rather nice 

and canonical we need switches for these things get on the ball guys

---

### Post by hansdown on 2011-10-16
Nice work, dusanyu.

Glad you fixed it.

---

