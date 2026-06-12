---
title: "I'd like to compile my own kernel. Any advise?"
date: 2011-01-17
forum: General Help
---

### Post by uqbar on 2011-01-17
In the good ol' days (SLS, Slackware, Gentoo) I used to recompile the kernel as the first thing.
Now I'm running Maverick on an x86_64 laptop and would like to make the same.
My main fear is to leave something out of the kernel configuration that could make my system unusable. And before wasting time in compile-try-test cycles, I'd like to know whether there's some tutorial on how to do it under Ubuntu.
I've tried to search for this topic among these forums, but it seems I had no luck.
Any help, pointer and advice will be more than welcome.

---

### Post by Brandon Williams on 2011-01-17
Google (search terms "kernel compile ubuntu") pointed to the kernel custom compile documentation [here](https://help.ubuntu.com/community/Kernel/Compile).

---

### Post by lithopsian on 2011-01-17
Just do it.  Keep your existing kernel and build a new one with a different name.  Keep the original in Grub so you can always boot.  Play around to your heart's content.  Keep a .config when it works, then you can go back if your next effort breaks it.  Lots of fun for all the family :)

Probably half of the kernel and 90% of the modules are unnecessary for most people.  Not much harm in keeping lots of modules around, except for compile time, but slimming down the kernel will improve performance at boot and use less memory.  A bigger benefit comes from compiling in modules that you always need, and you can optimise kernel and compile settings slightly for your hardware.

If you're worried about a starting point, take the .config for your existing kernel and then start tweaking.  It should just be sitting there in /boot.  Use make xconfig (needs quite a few qt-related dev libraries and tools), since the other methods are not manageable until you learn all the configs.

---

