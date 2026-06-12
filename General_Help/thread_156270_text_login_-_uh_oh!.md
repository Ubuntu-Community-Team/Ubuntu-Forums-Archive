---
title: "text login - uh oh!"
date: 2006-04-06
forum: General Help
---

### Post by dawhoo on 2006-04-06
I have an annoying problem.  It's not a deal breaker, but it sure is annoying.

Two days ago, I put in another HD to get some data.  After removing the HD, whenever I boot into Kubu, It boots into a text login.  Rather than login, I restart CTRL+ALT+DEL  When it restarts, it restarts in the graphic login - whew!

Is there something I can do to 'fix' this?  Was my putting in the other HD the cause of this and can it be undone?  

LIke I said, it's not enough of a problem to make me say 'goodbye linux based OS', but it's a little frustrating. I've never booted to text before, so I don't know what to do when I get to that screen.

---

### Post by aysiu on 2006-04-06
Next time it boots into text-only mode, log in and type ```
sudo /etc/init.d/kdm restart
```

---

### Post by dawhoo on 2006-04-06
that appears to have fixed it.   I've only tested it a few times, but three hard reboots and I'm still getting my graphic login. :D


thank you!!

I'm going to keep that piece of paper around for a while... just in case

---

### Post by aysiu on 2006-04-06
Why it stopped in the first place--who knows? I'm glad it's working now, though.

---

### Post by dawhoo on 2006-04-07
I spoke too soon.  The problem is back.  When I boot, it always goes to text now.

I disabled sessions in KDE, should I enable them again?  This is the only thing I can think of, that I've done, that might be causing the hiccup.

---

### Post by dawhoo on 2006-04-09
text login issues continued, so I reinstalled.  It's so easy to install, it seemed like the thing to do.  I had changed and tinkered with so many things, finding the source may have been too much.  Reinstalled and everything is working beautifully :D

---

### Post by oolunchbox on 2006-04-10
I had found that when I was having that problem it was because of something I had done to my xorg.conf file.  After about 5 reinstalls I realized I should backup the file before I changed anythign and now when I get a text boot screen I can restore a working xorg.conf and figure it out.

---

### Post by dawhoo on 2006-04-11
good advice!  At this point in my linux learning, a fresh install is a learning experience.  Tinker till I break it, reinstall and don't make the same mistake twice.... or try not to make the same mistake 4 times :D

---

### Post by oshuhua on 2007-11-11
Hello there, I've just started using Ubuntu after downloading the install disc several months ago. I got into Feisty and loved it so tried upgrading to 7. 10. But now there's no graphical login screen; I put in my same old username and password and it seems to be accepted, but after that I just get a prompt. Sorry, I don't  know what I should do next to get into the desktop environment. 
If it is helpful, I was also very curious to try KDE desktop so I installed it. . .Not ENTIRELY sure if it took or not, though, as it looked to me to be much the same. Too new to be sure. 
Thank you so much for any assistance!!
Chris O'Brien

Using here a pentium 4 Acer machine. . .

---

