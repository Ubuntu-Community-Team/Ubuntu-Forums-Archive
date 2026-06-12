---
title: "Restart wireless after resume"
date: 2009-12-29
forum: General Help
---

### Post by staf0048 on 2009-12-29
Hey everyone,

I've had my desktop linked directly to my router for a while, but am considering moving my router to another section of my house.  I tried connecting to my router wirelessly and it worked fine, but after a suspend/resume cycle the network manager tells me there are no wireless networks availalbe (when there should be 8-10).  If I restart, everything works fine, it connects automatically to my router wirelessly and I'm off and running.  It only happens after suspend/resume.  It's almost as if my wireless card is not being reinitialized after suspend.

Is there a command I can use to restart my wireless card?  Also, to automate the process after resume I'm planning on creating a shell script, but don't know where to place the file...

Any advice would be helpful.  Thanks!

---

### Post by Xero Xenith on 2009-12-29
I'm no ninja-expert on the subject, but I have this exact same issue. I believe it's due to faulty suspend/resume for many, many BIOSes (or motherboards, or... whatever controls the suspending these days :P). I think it's because they're all proprietary and varied. More info here:

[http://brainstorm.ubuntu.com/idea/94/](http://brainstorm.ubuntu.com/idea/94/)

It's the 94th ever idea on Brainstorm, and the second most popular. It's just something that needs more work, AFAIK :/

---

### Post by staf0048 on 2009-12-29
So the only option I have is to restart my computer every time?  There are no commands/scripts I can use for this?  Nothing like: 

sudo /etc/init.d/gdm restart - except for a network card???

---

### Post by a0u on 2009-12-29
Have you tried:
```
sudo /etc/init.d/networking restart
```

---

### Post by staf0048 on 2009-12-29
> **a0u said:**
> Have you tried:
```
sudo /etc/init.d/networking restart
```

Yeah, no luck.  :-(

---

