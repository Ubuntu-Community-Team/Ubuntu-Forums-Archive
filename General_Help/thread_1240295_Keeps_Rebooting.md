---
title: "Keeps Rebooting"
date: 2009-08-14
forum: General Help
---

### Post by smurfnz on 2009-08-14
I have a computer that has been running kubuntu 9.04 for about a month.  A few days ago it stopped working.  Durring the boot it goes through the grub loader fine and then pauses for a short time saing starting up.  It then gives an error message [ 7.85xxxx] Not Responding, and then reboots.  (The xxxx are different numbers each time.)  I tried the recovery mode and it pauses for a while on the processor and then flashes a full screen of information up and reboots before i can see any of it.  I have tried the install CD which loads to the menu. I then try the &quot;try kubuntu without installing&quot; option, hoping to get in and see if my drive can mount.  It gives me the same error.  I then tried an install, same error.  I have a utility CD with memory, processor, and hard drive tests which i have run.  All have passed.  I am at a bit of a loss as to what to test next.  Any troubleshooting help would be greatly appreciated.

---

### Post by smurfnz on 2009-08-19
On the off chance that anybody else has this error, i finnaly found what it was.  This computer is in a server rack and i had just recently put in a new KVM switch.  If i unplug the mouse cable from the computer it works.  I can plug the same mouse directly in without the switch and that works too.  I just can't use the mouse through the KVM switch.  I have other machines with the same version kubuntu on them that are not having this problem, so it has to be some sort of interaction between the motherboard and that KVM when the mouse gets initialized on bootup.  I did try a different open port on the KVM and same problem, i may try one of the ports that is plugged into a working machine and see if that works.  I will update when i try that.

---

