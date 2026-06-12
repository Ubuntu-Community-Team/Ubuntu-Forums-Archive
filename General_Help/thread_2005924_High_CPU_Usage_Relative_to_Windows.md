---
title: "High CPU Usage Relative to Windows"
date: 2012-06-18
forum: General Help
---

### Post by Jeff9 on 2012-06-18
Just as the title says, I've had Ubuntu 12.04 installed for a few days now and I'm noticing that the CPU usage is generally higher than in Windows in many scenarios. For instance, on a blank desktop without Firefox or anything running, I'm seeing CPU usage of around 15-20% (using System Monitor). Surfing Firefox yields usage that lingers between 20-40%. Again, both of these figures are somewhat higher than they were in Windows. The process that's always eating a portion of the CPU usage is "compiz".

Any help would be greatly appreciated!

Relevant Specs..
64-bit OS
E8500 @ 3.16GHz
4GB RAM
NVIDIA 520GTS

---

### Post by vasa1 on 2012-06-18
> **Jeff9 said:**
> ... The process that's always eating a portion of the CPU usage is "compiz".
...
compiz does consume resources. If you really don't need the enhancements compiz brings, you could try logging into Unity 2D.

---

### Post by zero2xiii on 2012-06-18
> **Jeff9 said:**
> Just as the title says, I've had Ubuntu 12.04 installed for a few days now and I'm noticing that the CPU usage is generally higher than in Windows in many scenarios. For instance, on a blank desktop without Firefox or anything running, I'm seeing CPU usage of around 15-20% (using System Monitor). Surfing Firefox yields usage that lingers between 20-40%. Again, both of these figures are somewhat higher than they were in Windows. The process that's always eating a portion of the CPU usage is "**compiz**".

Any help would be greatly appreciated!

Relevant Specs..
**64-bit OS**
E8500 @ 3.16GHz
4GB RAM
NVIDIA 520GTS

Hay,

It's a common-ish fact that 64-bit OS's has higher CPU usage than their 32bits counter parts. Especialy under linux/ubuntu. I have first hand experience with this in 12.04_64bit. My computer even seems "laggy" sometimes compared to 12.04_32bit.

Also compiz does eat some resources, I agree with above poster, if it is a "problem" disable compiz.

Cherz

---

### Post by pbrane on 2012-06-18
> **zero2xiii said:**
> Hay,

It's a **common-ish fact** that 64-bit OS's has higher CPU usage than their 32bits counter parts. Especialy under linux/ubuntu. I have first hand experience with this in 12.04_64bit. My computer even seems "laggy" sometimes compared to 12.04_32bit.

Also compiz does eat some resources, I agree with above poster, if it is a "problem" disable compiz.

Cherz
I don't have any of those issues. I'm running Xubuntu 64 and I have been running Ubuntu 64 bit for several years and never had any higher system load than I did with 32 bit Ubuntu or Redhat.

Compiz will eat CPU time if you don't have GPU hardware support for some of the compiz effects.

You should try running without compiz and compare the load. Are you using the nvidia drivers or nouveau drivers? nouveau does not have good 3D support at this time.

---

### Post by QIII on 2012-06-18
Could you install htop in the terminal
```
sudo apt-get install htop
```and then run it
```
htop
```Highlight the text and press cntr+shift+c to copy it and post the text back here between code tags (click the pound sign just above the input box to get the code tags automatically.)

It *could be *a lot of things.  What we are concerned about it what it *is.*

Everything is speculation until we see what is actually going on.  Compiz does consume resources but generally not enough to make your CPU sweat.

---

### Post by 3Miro on 2012-06-18
You have a dual core CPU and the first thing to check is how "20%" of usage is interpreted. I think Windows takes 50% to be one core used to the max and 100% for both cores. The default System Monitor for Ubuntu would read per-core usage, i.e. 20% means 20% of one core which is equivalent to 10% reading under Windows.

Also, the Gnome-System-Monitor that you are using can by itself take quite a bit of resource. I am not sure why, but to be sure you should try the lighter LXTask or the terminal ones like "top" and "htop".

All of those (Gnome System Monitor, LXTask, top and htop) will show both the CPU usage and the process that uses the most of the CPU. Maybe you have a rogue process going on.

---

### Post by vasa1 on 2012-06-18
> **pbrane said:**
> ...
Compiz will eat CPU time if you don't have GPU hardware support for some of the compiz effects.
...
Does the output from this command allow one to know about GPU hardware support?
```
/usr/lib/nux/unity_support_test -p
```

---

