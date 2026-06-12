---
title: "CPU Scaling"
date: 2009-07-25
forum: General Help
---

### Post by nmaster on 2009-07-25
I have the CPU scaling icon on my top panel.  I want the default for both CPU0 and CPU1 to be 'Conservative.'  However, whenever I reboot they go back to 'OnDemand.'  How can I make 'Conservative' the default?  Thanks.

---

### Post by nmaster on 2009-07-25
UPDATE: I just turned my laptop on and the CPUs were on 'Performance.' What's the deal?

---

### Post by hibliss on 2009-07-25
What type of computer is this. Most laptops have preset settings of high performance for CPU and Brightness while plugged in and they start going in to conservative mode when on battery power.

---

### Post by nmaster on 2009-07-25
> **hibliss said:**
> What type of computer is this. Most laptops have preset settings of high performance for CPU and Brightness while plugged in and they start going in to conservative mode when on battery power.

ah okay that makes sense with regards to my update.  it was plugged in when i booted this time, explaining the 'performance' setting.  when on battery however, it goes to ondemand instead of conservative.  i have a compaq presario c700.  btw, does cpu scaling happen like this on vista (or windows in general)?  just curious.

---

### Post by hibliss on 2009-07-25
It depends on the CPU and the setup. 

I can tell you that for my Eee, there are 3 settings, 1ghz, 1,33ghz, and 1.66ghz. Depending on how I set the power consumption, there are presets for screen brightness, fan speed, CPU scaling, and whether bluetooth is on or off. 

These are ACPI settings specific to the Eee, but there may also be specific settings for your model by default on install. Does your screen dim when you unplug your charging cable?

---

### Post by nmaster on 2009-07-25
> **hibliss said:**
> Does your screen dim when you unplug your charging cable?

no it doesn't.  i think you're right, its because of the power settings. 

btw, this isn't a huge problem, more of a curiosity.

---

### Post by nmaster on 2009-07-26
I was able to make conservative the default cpu governor by doing this:

```

sudo emacs -nw /etc/init.d/ondemand

```Found the line that says 
```

echo -n ondemand > $CPUFREQ

```and changed 'ondemand' to 'conservative'  

Now conservative is the default cpu governor.



NOTE: I just happened to use emacs.  Replace 'sudo emacs -nw' with 'gksudo gedit' if you are uncomfortable with emacs.

---

