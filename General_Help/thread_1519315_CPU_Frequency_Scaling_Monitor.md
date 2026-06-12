---
title: "CPU Frequency Scaling Monitor"
date: 2010-06-28
forum: General Help
---

### Post by techguy7 on 2010-06-28
I am new to ubuntu.  I have just one question, everytime I reboot my laptop the CPU Frequency Scaling Monitor goes back to "On Demand."  Why is that and can I also set it so it stays on Performance.  Thank you

---

### Post by lukeiamyourfather on 2010-06-28
Just saw this, and have wondered the same thing. Very annoying when booting my laptop and then battery says "low" after 2 hours instead of 5 hours because processors are still running at 2.0GHz instead of 800MHz on battery. I've checked the power settings and don't see any options relative to the processor speed. Looking forward to seeing replies. Cheers!

---

### Post by dcstar on 2010-06-28
> **techguy7 said:**
> I am new to ubuntu.  I have just one question, everytime I reboot my laptop the CPU Frequency Scaling Monitor goes back to "On Demand."  Why is that and can I also set it so it stays on Performance.  Thank you

To hack the change permanently (bad idea):
```
gksudo gedit /etc/init.d/ondemand
```

Your system automatically uses as much CPU as it needs, it is silly to change this unless for some reason it does not work.

---

### Post by Phazenator on 2011-03-08
It seems like a terrible design decision to allow the user to choose the CPU frequency scaling policy, but then not to retain the user's preferences during a reboot. The ability to allow a user to choose the scaling policy is there for a reason, and deciding that that reason can somehow be discarded on reboot is ridiculous.

Some user cases for which this isn't desired:

A power user who wants the fastest response time regardless of CPU usage and may not care at all about how this affects my CPU's maximum lifetime.

A laptop owner whose laptop suffers from overheating problems or low battery duration, and who may chose to run it at powersave all the time even if 70% of the time the computer is at 100% CPU.


I'll gladly be removing the ondemand script and replacing it with my own powersave script. I agree that it's a bad idea to have each user have to do this, and I hope this is changed in future Ubuntu releases.

---

### Post by darkhelmetchris on 2011-03-19
> **dcstar said:**
> Your system automatically uses as much CPU as it needs, it is silly to change this unless for some reason it does not work.
I agree with dcstar, but only partly.

While I agree that it is silly to change this unless for some reason it does not work, I think it's worthy to note that there may be circumstances when it is simply undesirable.  Others here have mentioned situations with laptops, battery life, and heat dissipation.  I would like to chime in and say that my own reasons for wanting a "sticky" CPU scaling monitor are valid -- even if only to me.  I agree that, for the average user, it's trivial.  I use my Atom-based netbook with Ubuntu every day for my job.  Battery life is my primary concern and heat is only a mild concern.  Both of these things are much more important than how fast my CPU goes, and when.  I like the idea that I can scale-up when needed, and scale-back when I wish to maximise my power utilisation.  I do not wish to have my CPU scaled to a faster setting for any reason except my choosing.  Granted, I understand this is certainly not the "normal" for most people, and is my own wish.

My Ubuntu, like others, boots up in "on-demand" mode.  For me, that is undesirable.  I want it to start in the lowest possible cpu scale, and stay at that scale.  I only want it to go faster when I specifically choose that.  It's clear to me here how to remove the on-demand script, but what I'm uncertain of is this:  if I remove the script, does the system maintain my setting indefinitely?  If I set it for "slow" will it stay there?

---

