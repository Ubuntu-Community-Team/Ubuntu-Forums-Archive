---
title: "Ubuntu will not start anymore..."
date: 2010-09-14
forum: General Help
---

### Post by gwu777 on 2010-09-14
I am on Ubuntu 10.4, I was playing around trying to get my mouse pad to work and now everything is broken!

Using synaptic, I removed most of my obsolete entries - cannot remember what they were - sorry.

Now ubuntu doesn't start, sometimes after waiting over 5 min, I get the following message:

Ubuntu is running in low-graphics mode.
Your screen, graphics card and input device setting could not be detected correctly. you will need to configure them yourself.

None of the option presented to me work, ie - run ubuntu in low graphic mode (it hangs)
-reconfigure the devices - (nothing happens)
-restart x (it hangs)

If I select the ubuntu recovery mode, nothing happens, it just hangs.

I have tried to see the verbose while starting by removing the quiet splash from grub, nothing happens, it just hangs.

So you have my problem, a lot of hanging!

Any bright ideas on what is missing and how i can reinstall it as I haven't been able to reach a console so far. (ALT+F1 and so on do not give me a console, just a blank screen.)

Thank you for your help and time...

---

### Post by Lateralis on 2010-09-14
Unfortunately, I don't know exactly how to fix your problem, but if you want a console to investigate, you may want to try aadding a 3 to the end of the kernel line in grub (press 'e', select 'kernel' line on next page and add the 3 to the end... I guess you know this already...).  You will (hopefully)  boot up in multi-user mode but will not initiate X.

---

### Post by gwu777 on 2010-09-14
Still no console, but thank you for your help. Surely there is another solution rather than installing eerything again, this is linux, everything is possible with a liveCD...

---

### Post by Chris1274 on 2010-09-14
> **gwu777 said:**
> Still no console, but thank you for your help. Surely there is another solution rather than installing eerything again, this is linux, everything is possible with a liveCD...

That depends on what you removed. You may have accidentally removed some system-critical packages, in which case a complete reinstall may be necessary.

---

### Post by wilee-nilee on 2010-09-14
If you choose the recovery in grub and you get to the recovery screen the last choice is a net active terminal if your plugged in with ethernet. I would start there with with a update a upgrade and reloading your desktop.


> Using synaptic, I removed most of my obsolete entries - cannot remember what they were - sorry.

Things can be done from a live cd but it is not a magical process you have to know what you have done, your lack of remembrance may end up being a learning lesson to remember; eh. ;)

---

### Post by gwu777 on 2010-09-16
> **wilee-nilee said:**
> Your lack of remembrance may end up being a learning lesson to remember; eh. ;)

Indeed!

I have now reinstalled my system. Good exercise! From what I have read, it is my use of various way to install programms that cause the auto-remove from synaptic to remove important software. **Apparently, in a nutshell, when I install soft. using apt-get, it doesn't get logged the same way by synaptic, who sees it has obsolete and OK to remove. **Conclusion, always use the same option to install and clean your system, I am now using apt-get only, hoping not to see this problem again. Promise, though I shall be more carefull before uninstalling a bunch of "obsolete" package. :D

---

