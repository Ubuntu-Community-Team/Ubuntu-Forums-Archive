---
title: "Compiling kernel with bare minimum options"
date: 2010-11-10
forum: General Help
---

### Post by kseise on 2010-11-10
I am looking to compile a kernel for my system which is a home built machine.  This machine is stable and has not had any hardware changes in the past 2 years.  I am trying to figure out exactly what modules and options to include in my custom kernel.  Is there a way to see what modules are actually in use on my system and build a custom kernel based on that?

---

### Post by 3Miro on 2010-11-10
```
 sudo lspci -v 
```

This will list everything that is being used. Before you rebuild the kernel you can check if the specific module will be compiled by looking at:

```
 cat .config | grep module_name 
```

.config is the Linux kernel configuration file for the specific kernel that you are building.

---

### Post by cek on 2010-11-10
Unless the default kernel has options disabled that you need, what are you expecting to gain from doing this?  The default kernel builds all optional pieces as modules, so what is loaded at startup time is the set of modules that you actually need.  I haven't measured, but I assume there is very little difference between building things as modules vs. as built into the kernel.

---

### Post by 3Miro on 2010-11-10
There are things that you can  gain from a custom kernel, depending on what you are doing. I once got 8% improvement simply by tweaking some parameters. Once you are going to make your own kernel, there is no point in compiling all the modules that you are not going to use anyway.

---

### Post by meijer.o on 2010-11-10
Sometimes it can be necessary to compile your own kernel, e.g. when you need a specific patch for your hardware.

If you want to make a lean kernel try this:

make localmodconfig  in order to get a .config file based on the loaded modules of the active kernel.

Kind regards,

otto meijer

---

### Post by kseise on 2010-11-10
I was looking for a speed boost, but now you have made me curious as to what sort of boost I would actually see.  Thank you both for the answers and insight.

---

