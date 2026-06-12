---
title: "Can't install drivers"
date: 2010-11-04
forum: General Help
---

### Post by saviouz on 2010-11-04
Hi, I recently installer Ubuntu 10.10 Netbook remix on my laptop. And now I can't get the "Additional Drivers" program to find my Broadcom STA Drivers! I am connected with the ethernet cable, but nothing happens after I open the program.
Which is weird because it worked perfectly on 10.04.

So I tried to install the driver by myself using the terminal, following the instructions included with the drivers. But when I typed the command "sudo insmod /home/saviouz/path/ wl.ko" nothing happened.

What can I do?

---

### Post by gandaran on 2010-11-04
did you update the software package list before looking in hardware drivers for the broadcom driver?
you can also use synaptic package manager to install Broadcom STA drivers, look for it there and mark for install.

---

### Post by efflandt on 2010-11-04
> **saviouz said:**
> But when I typed the command "sudo insmod /home/saviouz/path/ wl.ko" nothing happened.

Is wl.ko actually in a directory called **path** and why is there a space before wl.ko?  One (or both) of those two things could trip you up.  You should use the actual path to wl.ko with no spaces in that path.

---

### Post by saviouz on 2010-11-04
> **efflandt said:**
> Is wl.ko actually in a directory called **path**  and why is there a space before wl.ko?  One (or both) of those two  things could trip you up.  You should use the actual path to wl.ko with  no spaces in that path.
Of course that was just a quick example to make clear what command had no effect

> **gandaran said:**
> did you update the software package list before looking in hardware drivers for the broadcom driver?
you can also use synaptic package manager to install Broadcom STA drivers, look for it there and mark for install.
I did it. And i'm starting to worry, I read some guides and I'm sure by now I have installed the drivers. But I'm thinking that maybe my WLAN stopped working because in the lspsi output I don't see "network controller" or "broadcom".

---

### Post by saviouz on 2010-11-04
Yes! That was it! I opened the netbook and found out that I slightly moved a cable when I repaired the hard drive.

I knew installing a driver couldn't have been that hard XD
Sorry for the waste of time

---

