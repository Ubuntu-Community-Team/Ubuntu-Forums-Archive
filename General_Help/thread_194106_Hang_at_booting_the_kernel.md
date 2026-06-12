---
title: "Hang at booting the kernel"
date: 2006-06-11
forum: General Help
---

### Post by a42n81 on 2006-06-11
I have just attempted to install Ubuntu 6.06 Dapper three times.

Each time I downloaded an ISO image and burned a coaster.

The first time, I downloaded an image I think from osuosl. I got an error during install:

file:///cdrom/pool/main/u/ubuntu-keyring/ubuntu-keyring_2005.01.12.1_all.deb was corrupt.

So then I downloaded from [www.softpedia.com](www.softpedia.com).

After the install,  booting hung at the point

boot
Uncompressing linux... OK, booting the kernel

I tried a third download, this time from ubuntu.cs.utah.edu. 
Same results.

The machine I used for these attempts is a

VIA C3 800A EPIA-SP

During POST, it reports 458752K ram and 64M Shared Memory.

---

### Post by confused57 on 2006-06-11
Here's a great tutorial for burning an iso, if that's your problem:

[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by a42n81 on 2006-06-11
[QUOTE=confused57]Here's a great tutorial for burning an iso, if that's your problem:

[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)[/QUOTE]


Nope, I burned the ISO fine. The second and third installs went without a hitch. But the result was, the computer won't boot.

---

### Post by InsanePenguin08 on 2006-06-11
Hmm, I just got the same issue.  My Dapper was working great, but I rarely turn it off.  After opening up my computer to check something, I started to boot  it back up, but it hung at booting the kernel.  The only thing I did was check RAM, didn't change anything about the RAM or what have you. 

I seem to remember having rebooted a couple of times since I upgraded to Dapper, all without issues.

---

### Post by InsanePenguin08 on 2006-06-11
Hmm, ok, I fixed what seems to be the issue.  I had gone into my boot menu to check something else about the RAM I have installed, and went and changed the processor speed from "Normal" to "Compatible".  For some reason Linux did not like this change, and when I switched it back it booted up just perfect!

Just something for you to check, hope it helps somehow!

---

