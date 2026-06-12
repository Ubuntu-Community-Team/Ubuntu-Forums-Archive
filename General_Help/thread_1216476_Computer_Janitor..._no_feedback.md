---
title: "Computer Janitor... no feedback?"
date: 2009-07-18
forum: General Help
---

### Post by Jeinhor on 2009-07-18
I start the computer janitor, but it does not tell me anything. Does that mean it's okay?

---

### Post by Yannick Le Saint kyncani on 2009-07-18
You may try gtkorphan instead, but don't make mistakes and bork your system.

---

### Post by UbuntuNerd on 2009-07-18
I haven't use the "Computer Janitor" but here is what I have in mine if you feel like doing some cleaning look at this [guide](http://my.opera.com/ubuntunerd1/blog/keeping-ubuntu-clean)

---

### Post by NightwishFan on 2009-07-18
(As far as I know) Computer Janitor finds potentially outdated or manually installed packages. It sort of extends the function of apt-get autoremove.

I would say you are fine, and no action is to be taken.

---

### Post by Jeinhor on 2009-07-19
Okay, thank you for the information everyone!

A suggestion might be to add some feedback if there's no cleaning to be done. For example: "Your computer is clean" =)

---

### Post by Rozzalyn on 2009-07-22
Mine does work and I was wondering what packages are safe to clean up, I read through the ones that said that my system would not be affected if I removed them. I deleted those and kept the ones that I was unsure of.

Is there a reference guide to find out if my system would not be harmed by deleting those extra packages? or do I have to manually look them up in the synaptic package manager?

---

### Post by NightwishFan on 2009-07-22
The most common packages that it lists are either ones that were manually installed or ones that are unneeded dependencies. If you did not manually install .deb files, then I would say they are safe to clean up. It you are worried is a bit safer to just use the command:

```
sudo apt-get autoremove
```

That command would not remove anything you might need and it will clean up unused dependencies.

---

