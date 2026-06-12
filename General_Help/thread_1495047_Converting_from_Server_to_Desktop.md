---
title: "Converting from Server to Desktop"
date: 2010-05-27
forum: General Help
---

### Post by jmoesch on 2010-05-27
I have been running Ubuntu 7.04 i386 Server Edition (Linux version 2.6.20-15-server (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:41:34 UTC 2007), running on a Intel Celeron 2.66 with 1gb RAM as an office file server for about 3 years now.  It has been mostly very successful.  I have installed and played with lots of things, but as it has settled in the only thing we are doing with this machine is serving files for a Windows network.  For that we are using two dedicated hard disks in a RAID1 array (with a cold spare available) using mdadm and running SAMBA.  That’s working great.  The OS is installed on a separate 80gb HD.  

However, I really want to switch to a the graphical desktop version of Ubuntu.  I don’t fool with it enough to get good at the command line.  Also, I’d like for another person in the office to be able to work with the server if needed, and a graphical interface will make that much easier.  I am not too concerned with any performance drop using desktop, because the load on this machine is relatively light.  

My question is how should I go about this to minimize the pain?  I tried just updating and then “apt-get install ubuntu-desktop”, but that failed because I think the repositories I have listed are probably out of date.  In addition, it would be nice to convert to the most modern version of Ubuntu.  

I’ve researched of course and made preparations.  I have copied the Samba file, the mdadm info, and a lot of other information to another computer in case things go badly.  My plan is to just install the new OS on the 80gb HD, and leave the current one alone, and then using GRUB later I could boot to the old one if I don’t get it right the first time.  Then install and configure mdadm and samba.  

I would appreciate any hints or comments anyone can throw my way.

---

