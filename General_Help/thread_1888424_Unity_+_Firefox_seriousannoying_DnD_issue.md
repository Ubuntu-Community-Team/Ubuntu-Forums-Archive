---
title: "Unity + Firefox serious/annoying DnD issue"
date: 2011-11-29
forum: General Help
---

### Post by t1497f35 on 2011-11-29
Hi,
In 11.10 I get random Unity/desktop freezes when I drag something from inside Firefox **while its window is maximized**. I wonder (and hope a lot) that this is addressed in 12.04. **Does anyone know if it's reported as a bug anywhere** **to be fixed before 12.04 ships**?

Here's what I think happens:
When starting to drag something in Firefox, Unity's vertical bar, for whatever reason, starts reacting to this drag operation (probably showing which apps can process the drag) despite the fact that the mouse is far from the vertical bar.
This freezes the Unity desktop completely, the time is random, sometimes for half a second, sometimes for like 5-10 seconds which is really embarassing, especially since my computer is powerful (GTX 560Ti, Core i5 etc).

Attached a small video where the desktop freezes for like 1-2 seconds (sometimes I get up to 10 sec), that's annoying since this is Unity-specific and cause Unity is supposed to make the desktop better and more responsive or at least keep it as responsive as before. Not ranting, just explaining.

---

### Post by effenberg0x0 on 2011-11-29
> **t1497f35 said:**
> Hi,
In 11.10 I get random Unity/desktop freezes when I drag something from inside Firefox **while its window is maximized**. I wonder (and hope a lot) that this is addressed in 12.04. **Does anyone know if it's reported as a bug anywhere** **to be fixed before 12.04 ships**?

Here's what I think happens:
When starting to drag something in Firefox, Unity's vertical bar, for whatever reason, starts reacting to this drag operation (probably showing which apps can process the drag) despite the fact that the mouse is far from the vertical bar.
This freezes the Unity desktop completely, the time is random, sometimes for half a second, sometimes for like 5-10 seconds which is really embarassing, especially since my computer is powerful (GTX 560Ti, Core i5 etc).

Attached a small video where the desktop freezes for like 1-2 seconds (sometimes I get up to 10 sec), that's annoying since this is Unity-specific and cause Unity is supposed to make the desktop better and more responsive or at least keep it as responsive as before. Not ranting, just explaining.

I have justed tested it, but couldn't reproduce a behavior such as you report. I've seen the movie you attached. Can you give me some more info about your environment? 

lsb_release -a
uname -a
nvidia-settings
compiz --version
unity --version

Thanks,
Effenberg

---

### Post by t1497f35 on 2011-11-29
Yes, I'm very interested into helping solving this issue.
Notice, I'm using 11.10 but I'm pretty sure it's not fixed in 12.04, I'll grab asap a 12.04 daily build and make sure it's not fixed there either.

```

fox@fox:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

``````

fox@fox:~$ uname -a
Linux fox 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```nvidia-settings - I'm using driver version 290.10 x86_64 from Nvidia's site (Ubuntu's 280x driver behaves the same way), graphics card: GeForce GTX 560Ti.

Compiz 0.9.6
unity 4.24.0

Details about my desktop hw (sudo lshw >> hw.txt) is attached.

EDIT: Finished checking, it's **not** fixed in Ubuntu 12.04.

---

### Post by cariboo on 2011-11-29
Moved to General Help, as this has nothing to do with Precise.

---

