---
title: "Cannot configure Nvidia graphics card"
date: 2010-05-20
forum: General Help
---

### Post by lanceman63 on 2010-05-20
When I start my computer I get the following errors: "Could not open the device file.", "Failed to initialize the Nvidia graphics device PCI:1:0:0." and "Screens found but none have a usable configuration." I have been to the site [http://wiki.x.org.wiki](http://wiki.x.org.wiki) and checked each of the error messages mentioned above. One of the solutions tells me to check the log file. When I try to do that I am told the log file cannot be found. I would think the graphics card wasn't being detected but since I get warnings that the card is not working I know that the computer knows it's there. My graphics card is a GeForce Advanced Graphics Card in an Advanced Graphics Port. How do I fix this?

Thanks,

Lanceman63

---

### Post by lanceman63 on 2010-06-03
So far unanswered.

Thanks,

Lanceman

---

### Post by Chronon on 2010-06-03
You could mention which specific model your card is and whether this started suddenly.  Does the LiveCD run properly?

---

### Post by lanceman63 on 2010-06-03
Sorry, it's an Nvidia GeForce 6300 A-LE. I have been to the Nvidia website and although they support Linux for some of their products, I cannot find a Linux driver for my graphics card.

---

### Post by arsenic23 on 2010-06-03
Did you get this error right after installing ubuntu?
Did you get it after enabling the Nvidia driver?
Did you get it after an update?

Did you ever get a GUI?
Does the live CD work?

What version of ubuntu are you using?

---

### Post by dcstar on 2010-06-03
> **lanceman63 said:**
> Sorry, it's an Nvidia GeForce 6300 A-LE. I have been to the Nvidia website and although they support Linux for some of their products, I cannot find a Linux driver for my graphics card.

I think you have highlighted the problem right there, there is no Linux driver from Nvidia so you will have to use the generic "nv" driver with your Ubuntu system.

This means you won't get any hardware acceleration and desktop effects won't work.

It may be time to consider obtaining a supported video card if you want the full Ubuntu capabilities.

---

### Post by lanceman63 on 2010-06-03
Thanks. I don't have the money for another graphics card so I guess I'll just have to live with it.

Thanks

---

