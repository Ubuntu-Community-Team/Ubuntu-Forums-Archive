---
title: "VirtualBox shuts down computer during Win7 RTM install"
date: 2009-08-15
forum: General Help
---

### Post by cmost on 2009-08-15
Hi guys!  I previously installed the Windows 7 RC in VirtualBox and when the RTM version of Win7 Professional became available to an IT friend of mine I attempted to install it to check out Microsoft's latest and (greatest?)  I created a new virtual machine in VirtualBox 3.04 running on Ubuntu Jaunty 9.04 64Bit.  I gave the VM 1024 of my 4 GB of RAM, a 20 GB dynamic HD and 128 video memory (3D acceleration enabled.)  I have a similarly configured XP Pro VM that works fine (but I've had it setup for ages!)  During the installation of Win7, it gets to the point of expanding the setup files; somewhere around ~60% the entire computer shuts down.  And it crashes hard!  As in the computer unceremoniously turns off!!!  Even the motherboard loses power as my USB drives' lights go off, which doesn't even happen when I do a clean shutdown.  I've duplicated this bug three times and I don't want to do it again.  Any ideas why this is happening?  I'm not sure what logs to pull.  I'm running Kernel 2.6.30.4 at the moment.  I think when I installed the RC, I was using the 2.6.29.6 Kernel.  Could this be the issue?  I've tried Googling but nobody else seems to describe this problem.  I thought I'd get the opinion of the forum before monkeying with Kernels.  Thanks!

---

### Post by blueridgedog on 2009-08-15
As a debugging step, you could try the RC again and see if it reproduces the error.

---

### Post by cmost on 2009-08-16
Excellent suggestion.  Also, I've updated to the 2.6.31-RC6 Kernel and was able to reproduce the crash.  I'm also going to poke about in the logs to see if I can learn any clue.  Thanks.

---

### Post by cmost on 2009-08-19
*** Bump ***

Okay, I tried reinstalling the RC and VirtualBox crashes.  I also tried the 2.6.31-RC5 and 2.6.30.5 Kernels to no avail.  I also downgraded my Nvidia driver from 190.18.3 to 180.60 to see if that made any difference...no dice.  My suspicion is that version 3.0.4 of VirtualBox has a bug as I believe I was on an earlier version when I initially installed Win7 RC.  My next move is to downgrade VirtualBox to an earlier version and see if it still crashes with Win7.  As a final thought, I could go all the way back to Kernel 2.6.29.6 as I believe I was using that Kernel when I initially installed Win7 RC.  Any other thoughts?  Seems like the community here can't handle anything but super easy questions...  :(

---

### Post by blueridgedog on 2009-08-19
Based on the steps you posted, the only item that remains is the version of VirtualBox.  I suggest you post or search at VirtualBox forums:

[http://forums.virtualbox.org/viewtopic.php?f=19&t=19903&start=0](http://forums.virtualbox.org/viewtopic.php?f=19&t=19903&start=0)

---

