---
title: "wireless firmware acer"
date: 2012-08-21
forum: General Help
---

### Post by sonofmylover on 2012-08-21
I downloaded LUBUNTU and tried to install it on my computer with UBUNTU on it.  It said the wireless  firmware is missing.  It is working for UBUNUTU but not for LUBUNUTU.  What should I do.  An ACER laptop.  Thanks

---

### Post by vandorjw on 2012-08-21
[COLOR="Red"]Please open a terminal and type:
```

lspci | grep net

```
and let us know what it says[/COLOR]

**Edit: Explain what the command does...Info only; only read if you are curious.**
1. ***lspci*** = creates a list of hardware found in your computer. A simular command is lsusb which gives a list of USB devices attached to your computer.
2. ***|*** = This is a pipe. It will take the output from the command in front of it, and give it to the command behind it.
3. ***grep*** = a toll/program that will search through plain-text until it finds what you are looking for.
3b. ***net*** = this is what we told grep to look for in the list of hardware, which is received from lspci

I hope that this made sense. I need to know the exact wireless hardware that you have, so that I do not accidentally tell you to install the wrong firmware.

Cheers - CC7

---

