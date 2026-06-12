---
title: "time not synching"
date: 2010-07-15
forum: General Help
---

### Post by goltoof on 2010-07-15
My time keeps getting thrown off by about 15 minutes. It corrects itself randomly but then goes back!  Not sure yet if it's decrementing slowly or if it takes 15 off all at once.

ntpdate ntp.ubuntu.com puts it back, output is:
```
15 Jul 08:09:29 ntpdate[6157]: step time server 91.189.94.4 offset 1056.199059 sec

```
Curious what the "offset" means.  

Is there a way to ensure it keeps constant time without having to do it manually?

---

### Post by dino99 on 2010-07-15
is your cpu overclocked or using some tweaked settings ?

---

### Post by sgosnell on 2010-07-15
Offset is the amount of correction made.  In your example, the time was adjusted by 1056.199059 sec, which would be 17.6 minutes.  I don't know what is causing the time to change on your system.

Install ntp, and ntpd will be run at startup and automatically correct your system time regularly, as well as teach the system clock.  The default is to use ntp.ubuntu.com, but you can change that to any server you like by editing /etc/ntp.conf.

---

### Post by goltoof on 2010-07-15
> **dino99 said:**
> is your cpu overclocked or using some tweaked settings ?

Def not overclocked, no tweaks I'm aware of.  The computer is brand new, with fairly fresh install (lucid).

---

### Post by goltoof on 2010-07-15
This is a real nuisance, it looks like it's getting worse, now 20 minutes off. It's not decrementing, it just suddenly takes off 20 minutes.

The docs say:> Why does NTP keep resetting/failing?
NTP attempts to fix your local clock to keep accurate time. If your local clock drifts too fast (usually HW problems or IRQ lockups or somesuch) then NTP either keeps resetting your clock or gives up and terminates. Fix the drift problem and NTP will behave. 
I'm not sure how to fix this "drift" problem.  Any pointers appreciated.

---

### Post by goltoof on 2010-07-15
> **sgosnell said:**
> Install ntp, and ntpd will be run at startup and automatically correct your system time regularly, as well as teach the system clock.  The default is to use ntp.ubuntu.com, but you can change that to any server you like by editing /etc/ntp.conf.

It's already installed, no matter how many times i sync it just goes back.  It looks like a "clock drift /double clock" issue, of which right now has no clear solution.

---

