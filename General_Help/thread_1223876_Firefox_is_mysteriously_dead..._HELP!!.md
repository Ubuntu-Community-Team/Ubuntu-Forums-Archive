---
title: "Firefox is mysteriously dead... HELP!!"
date: 2009-07-26
forum: General Help
---

### Post by drainplugofideas on 2009-07-26
I was using firefox one minute and then the next it won't start. All that happens is that firefox asks me if I want to load the previous session and then no matter what button I press, nothing happens. It's not in the system monitor and rebooting shutting down does not fix it. Shiretoko doesn't work either. I'm using Jaunty for the record.

Please help!!

---

### Post by tjwoosta on 2009-07-26
I assume you've tried reinstalling and rebooting?

Try doing this

first kill all running firefox processes
```
killall firefox
```

then run firefox from a terminal and copy and paste whatever error it gives you when it stops working into your next post
```
firefox
```

---

### Post by drainplugofideas on 2009-07-26
"
kevin@kcubuntu:~$ killall firefox
firefox: no process killed
kevin@kcubuntu:~$ firefox
Segmentation fault
kevin@kcubunt:~$ 
"

I did try reinstalling but not very well. All I did was go into synaptic and select firefox for reinstallation. What should I do next?

---

### Post by QIII on 2009-07-26
Try 

```
firefox -safe-mode
```

to see if it will run without add-ons and plugins.

---

### Post by drainplugofideas on 2009-07-26
> **QIII said:**
> Try 

```
firefox -safe-mode
```

to see if it will run without add-ons and plugins.

That seems to have worked. I went back and re-enabled a bunch of the extensions and so far everything is working. Thanks man

---

### Post by QIII on 2009-07-26
If you run into the problem again, you might want to look at the following.

It's old, but should still work.

[http://www.linuxquestions.org/questions/linux-general-1/ubuntu-and-firefox-segmentation-fault-657278/](http://www.linuxquestions.org/questions/linux-general-1/ubuntu-and-firefox-segmentation-fault-657278/)

---

