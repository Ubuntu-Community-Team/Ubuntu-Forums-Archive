---
title: "ethernet does not work"
date: 2006-03-21
forum: General Help
---

### Post by slim27616 on 2006-03-21
Okay this is a quik one. (I hope). 
but the story is not short. 

It start when i bought a gateway m275 earlier this year. And i went out linux distro shopping after my gentoo live cd failed to connect. So I went on to look online to see if anyone had written about installing linux on this laptop. I found a post that said that K/Ubuntu 5.04 worked but 5.10 did not. Well I new this was a kernel problem because if I simply loaded the dist-upgrade and used the older kernel, everything worked more or less fine. 


Now the only issue is I believe that the e100 module has been repaired(from reading other forums and running opensuse). So I've done a fresh install of 6.04(why not try the beta) only to find that it only had some significant acpi issues. So I decieded to attempt to boot 5.10. No problem it boots and as expect not internet access. Now i only need help with sept number 2. HOW DO I COMPILE LINUX KERNEL WITHOUT AN INTERNET CONNECTION? 

I do have windows on this computor so I can can download deb files and the kernel sourceses(which i have) to the computor. Im missing the things needed to compile the kernel and cant file the deb file online. I would need a list and so on. 

                                             thanks in advance
                                                     slim

---

### Post by slim27616 on 2006-03-22
please anyone i need to know the dependencies and where to download them. 
Also how to set up a repository on my own hard disk.

---

### Post by ozorba on 2006-03-22
Here how you compile your own kernel:

If you have a memory stick and it works under linux I suggest to copy the kernel source .deb file to it.

Install the kernel source .deb package with

sudo dpkg -i kernel?????.deb


then read this:

[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)


---

---

