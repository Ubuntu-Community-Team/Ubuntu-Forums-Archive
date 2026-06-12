---
title: "On screen keyvoard appeared from no-where"
date: 2012-02-13
forum: General Help
---

### Post by Jonners59 on 2012-02-13
I have just had an on-screen keyboard appear on my desktop from no-where.  It is getting in the way, even as I type.  I assume it comes from some Accessibility app, but I can't find where never mind why it has suddenly decided to start up!

Any ideas.

Discovered it is called Antler - keyboard icon on the image opened preferences, sadly did not include a kill key!!!!!!!!!!!!!!!!1

---

### Post by jerrrys on 2012-02-13
This seems to be a new package in 12o4.  If so, you should of posted in the Precise Forums.

Is it in your startup software list?  If so, just remove it.

---

### Post by Jonners59 on 2012-02-13
I am not using 12.04,but 11.10 so how did it get in there?

It is and was NOT in the start up apps.

I think I resolved the problem.  I went in to Ubuntu Software Centre and searched all keyboards and deleted all the on-screen apps, there were three.  Seems to have worked - for now.

---

### Post by HiImTye on 2012-02-13
if it pops up again just kill it
```
xkill
```
and then click on it. no need to find out what the class, name or PID is

---

### Post by jerrrys on 2012-02-13
Glad you found a fix, but this is why I thought its precise

[http://packages.ubuntu.com/precise/caribou-antler](http://packages.ubuntu.com/precise/caribou-antler)

No reference to anything else, maybe a ppa.  But no matter, its fixed

---

### Post by Jonners59 on 2012-02-13
Cheers guys
Yes, it's gone.  A sledge hammer to crack a nut ,maybe, but gone

---

