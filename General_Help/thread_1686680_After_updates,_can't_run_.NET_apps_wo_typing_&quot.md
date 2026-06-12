---
title: "After updates, can't run .NET apps w/o typing &quot;mono&quot; first"
date: 2011-02-12
forum: General Help
---

### Post by Ishpeck on 2011-02-12
I've been writing .NET programs on my Ubuntu system at home and on my Windows 7 computer at work.  It's been going well until just yesterday, I ran `apt-get upgrade` and now, when in a terminal, I type:

> $ ./myprogram.exe

... I get the following:


> bash: ./myprogram.exe: cannot execute binary file

I can run it with the following:

> $ mono myprogram.exe 

But I never had to do that before.  I tried using DotGNU and that didn't pan out.  Mono's site says I'd need a kernel module ... but I'm not sure where to get it. 

I'm not sure if the upgrade is to blame for this... it may be my fault but I need some more direction in my pursuit of solutions.  I'm just flailing around right now.

Edit:  I'm running lucid lynx, BTW.

---

### Post by directhex on 2011-02-13
is apt:binfmt-support installed?

---

### Post by Ishpeck on 2011-02-17
This is how I checked: 

> $ sudo apt-get install binfmt-support
Reading package lists... Done
Building dependency tree       
Reading state information... Done
binfmt-support is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by directhex on 2011-02-18
> **Ishpeck said:**
> This is how I checked:

And you have a /proc/sys/fs/binfmt_misc/cli file?

---

### Post by Ishpeck on 2011-02-18
> **directhex said:**
> And you have a /proc/sys/fs/binfmt_misc/cli file?

Nope.  The /proc/sys/fs/binfmt_misc/ directory appears to be empty.

---

### Post by Ishpeck on 2011-02-20
Following the instructions found [here]("http://www.mjmwired.net/kernel/Documentation/mono.txt") helped me.  Thanks for the help!

---

