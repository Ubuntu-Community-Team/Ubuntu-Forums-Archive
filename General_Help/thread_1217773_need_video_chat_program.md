---
title: "need video chat program"
date: 2009-07-19
forum: General Help
---

### Post by ARhere on 2009-07-19
Hello Everyone,

I am leaving for Texas on a contract and leaving my three little girls in Colorado and I am hoping to be able to see and talk with them using a simple IP to IP video chat program ***that works!!!***.

[color=red]I have tried Ekiga[/color] and no matter what, I cannot get it to register.  It just says "unable to register" with no other help.  [Here is the open thread]("http://ubuntuforums.org/showthread.php?t=1217589") but no one wants to touch it.

[color=blue]I saw a suggestion to use Twinkle[/color] but it does not seem to have a video option.

Please help with suggestions.  It is frustrating as hell and I leave in two days.

-AR

---

### Post by cosine352 on 2009-07-19
try this. works for me

> sudo apt-get install empathy

---

### Post by c0mput3r_n3rD on 2009-07-19
You can also check out skype.

[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

---

### Post by Twitch6000 on 2009-07-19
I would suggest skype.

However if you do not mind using a web app/site I suggest blogtv.

Its a small mostly mature site.

You can video chat and text chat with people.

---

### Post by PGScooter on 2009-07-20
If you have problems with skype, try skype-static and skype-static-oss. One of the three (including skype normal) should work. Best of luck with the move to Texas.

---

### Post by ARhere on 2009-07-25
I ended up trying Skype.  At first it crashed every time I used my webcam, but after a little goggling I learned to launch Skype with the following command...
```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

No problems what-so-ever after this.

-AR

---

