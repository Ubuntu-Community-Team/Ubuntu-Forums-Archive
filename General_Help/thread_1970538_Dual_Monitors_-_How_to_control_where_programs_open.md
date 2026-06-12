---
title: "Dual Monitors - How to control where programs open"
date: 2012-05-01
forum: General Help
---

### Post by djpemberton on 2012-05-01
I am running 12.04 with two monitors. Everything basically works well, except that I can't seem to control where a program will open. I have the launcher displayed on both monitors. While programs usually seem to open on the monitor whose launcher I am using, they still often seem to randomly open on the opposite monitor. Is there a way in which I can gain better control of this?

Thanks

---

### Post by oshirowanen on 2012-05-01
> **djpemberton said:**
> I am running 12.04 with two monitors. Everything basically works well, except that I can't seem to control where a program will open. I have the launcher displayed on both monitors. While programs usually seem to open on the monitor whose launcher I am using, they still often seem to randomly open on the opposite monitor. Is there a way in which I can gain better control of this?

Thanks

Can't answer your question, but I'm wondering if Unity remembers the last position of an application when closed?

---

### Post by lykeion on 2012-05-01
One thing you can do in a terminal is change the DISPLAY variable to your secondary monitor and launch your application.
 
To start up let's say firefox in your secondary monitor, enter these commands (in this example primary monitor is **:0.0** and secondary is **:0.1**):```
export DISPLAY=:0.1;firefox
```
When you close the terminal the DISPLAY variable will be reset to default (i.e. your primary monitor).

Hope it helps

---

### Post by djpemberton on 2012-05-02
> **oshirowanen said:**
> Can't answer your question, but I'm wondering if Unity remembers the last position of an application when closed?

I had already tried that with no luck. It is really weird. It seems that certain programs will consistently open on certain monitors. Then it gets even more weird. Skype opens on the right monitor, but the "call phones or send sms" window opens in the left monitor.

I would really like an easy way to make it where anything opened from the right monitor's launcher would open in the right monitor, and the other way around.

---

### Post by djpemberton on 2012-05-02
> **lykeion said:**
> One thing you can do in a terminal is change the DISPLAY variable to your secondary monitor and launch your application.
 
To start up let's say firefox in your secondary monitor, enter these commands (in this example primary monitor is **:0.0** and secondary is **:0.1**):```
export DISPLAY=:0.1;firefox
```
When you close the terminal the DISPLAY variable will be reset to default (i.e. your primary monitor).

Hope it helps

I'm not sure that would be the solution I'm looking for. Simply dragging the window where I want it after it opens would be quicker. Any other suggestions?

---

### Post by geo316 on 2012-10-13
shame there's no answer or at least insight regarding this - it's mildly annoying.

Dialog boxes are uncontrollable as well as far as which screen they open on. I've had apps appear frozen only to discover that an alert or dialog opened on the other monitor and then became hidden because it lost focus to something else...

Anyone have help?

G

---

### Post by Ichbinich on 2012-11-20
I am trying to find an answer to this problem too.

I already tried "devilspie" which is supposed to do stuff like this but it is not working well on my setup.

It can move windows onto the screen you want, but first of all you have to do a configuration for all programms one by one (which is quite annoying). Secondly, it does not even work constantly.

So I also would be really interested in an answer to this question....

---

