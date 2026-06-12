---
title: "Problem with expat package"
date: 2010-01-22
forum: General Help
---

### Post by AndreC on 2010-01-22
Hello

I'm a complete novice to Linux but I've been asked to help get a Texas Instuments Davinci development board going.  Unfortunately I have gotten stuck with so many obstacles, and things are not going well at the moment.  To use one of TI's components, I need to install the expat package.  Sounds simple... but here comes the trick:

When I run:
*sudo rpm -q expat*
package expat is not installed

but when I try to install it with apt-get (or with Synaptic Package Manager) I get the following:

andre@DaVinciHostLinux:~/expat-2.0.1$ *sudo apt-get install expat*
[sudo] password for andre: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**expat is already the newest version.**
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andre@DaVinciHostLinux:~/expat-2.0.1$ 

These two options contradict each other... and are really confusing!  Can someone please advise me on how to solve this issue?  

(This may be in the wrong category on the forum, but I don't even know enough of Linux to know what these packages form part of :) )

Regards

Andre

---

