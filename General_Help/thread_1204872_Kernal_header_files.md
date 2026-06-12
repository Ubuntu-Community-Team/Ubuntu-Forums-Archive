---
title: "Kernal header files"
date: 2009-07-05
forum: General Help
---

### Post by stewbee on 2009-07-05
So I am trying to install a university provided Cisco VPN program. However when I run the make file, make aborts and gives me an error that it can't find a particular header file. The file that I am looking for is 'skbuff.h'. After a bit of research on [http://lxr.linux.no/](http://lxr.linux.no/)  it looks like it should be part of the Linux kernel, but I cannot find it in the purported directory.

So my issue isn't so much with the specific problem of setting up the vpn, but a more general:

1 .How do I get these headers that appear to be part of the kernel but are not in the include directory?
2. Is there a way to do this though synaptic? (btw, searches in synaptic turned up nothing when looking specfically for the file in question, not that I expected it to do so)

I have little experience with getting files onto the PC if it is not in synaptic (ie. apt noob), so any help would be appreciated

tech info:
using  jaunty, gnome, kernel 2.6.28-11

Thanks in advance!

---

### Post by Cheesemill on 2009-07-05
Try doing:
```
sudo apt-get install linux-headers-`uname -r`
```This should download the headers for your current kernel version.

Or you can search for linux-headers using Synaptic.

---

### Post by stewbee on 2009-07-05
Cheesemill,

Thanks for the reply. This seemed to help, but now it looks like this has morphed into a make file issue. I will have to look into this some more. 

Thanks again!

---

### Post by Cheesemill on 2009-07-05
It can't hurt to make sure that the build-essential package is installed as it contains all the tools needed for compiling programs.

Also check the README file that came with the software and make sure that all required dependencies are installed.

---

