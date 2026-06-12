---
title: "Some beginners thoughts on 9.10"
date: 2009-12-21
forum: General Help
---

### Post by ubeone on 2009-12-21
Hi,
   I have installed Ubuntu 9.10 alongside Win XP and now have a dual boot PC, great. Whats not so great is that I cannot get my nice shiny new LCD monitor to do any better than 800x600, on XP it is set on 1280x720, which looks correct. I have searched the net in vain for an easy to understand answer to this problem. I have loaded the Nvidia drivers from package manager but they make no difference. It seems to me that the problem is that Nvidia will not give away the correct driver, hence the problem. I don't care why it does not work correctly, I just know it does not. If someone could offer a step by step solution to this problem I would be grateful.

---

### Post by Grenage on 2009-12-21
Hi there. First off, let's look under System/Administration/Hardware Drivers.  Does it display the driver as active?

After that, ensure the package nvidia-settings is installed.  Assuming that it is, then run it using:

```
gksu nvidia-settings
```

Assuming none of that works (you *may[I] need to restart X or just your computer after the change)*[/I], post back the results:

```
lspci | grep VGA
```

Along with your monitor make and model.  Xorg.conf is a last resort, since it's redundant in 9.10 (unless you have no other choice).

---

### Post by kestrel1 on 2009-12-21
It sounds like your xorg.conf file is not setup correctly.
I need to dig out some info, if you pm me I will get it over to you.

---

