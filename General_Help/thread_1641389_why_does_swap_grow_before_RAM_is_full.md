---
title: "why does swap grow before RAM is full?"
date: 2010-12-09
forum: General Help
---

### Post by pgagy on 2010-12-09
This is not an issue, but a question about how Linux organizes the swap file in general.

I recently upgraded my 512MB of ram to 1.5GB.  This helped improve the number of applications I can run before swap file is used, however, the swap file still grows under heavy usage, but the RAM never actually gets filled up.  For example, swap file grew to about 300MB, while ram had only about 800MB in it.  There was plenty of free ram (another 700MB before it was filled up), yet the swap file was already starting to grow.  Any idea why Linux chooses to use the swap file before my RAM is filled?  Is there any way I can play around with not having the swap file grow at all?

I'm monitoring all of this with the system monitor that comes with Kubuntu.

---

### Post by wilee-nilee on 2010-12-09
With that much ram I would adjust the swappiness.
[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_)

That is the best I can do the technical bits are well not really needed to be honest and will only be a pseudo answer at best, at least from me.

---

### Post by oldos2er on 2010-12-09
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by pgagy on 2010-12-09
You're right, swapiness is the answer.  In case someone searches for this, the solution is fairly simple.  I did this and the swap file is now under control!  

From the link oldos2 posted (To save you a click)

Basically, Swapiness is how much your computer uses the swap file.  Default in ubuntu is a value of 60.  If you have lots of RAM, you can reduce this to recommended value of 10.  Here's how you do it:

To check the swappiness value 
cat /proc/sys/vm/swappinessTo change the swappiness value - A temporary change (lost on reboot) with a swappiness value of 10 can be made with 
sudo sysctl vm.swappiness=10To make a change permanent, edit the configuration file with your favorite editor: 
gksudo gedit /etc/sysctl.confSearch for *vm.swappiness* and change its value as desired. If *vm.swappiness* does not exist, add it to the end of the file like so: 
vm.swappiness=10Save the file and reboot. 
 
[B]
[/B]

---

