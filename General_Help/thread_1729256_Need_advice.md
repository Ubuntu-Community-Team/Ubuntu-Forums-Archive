---
title: "Need advice"
date: 2011-04-14
forum: General Help
---

### Post by pvravi on 2011-04-14
Hi 

I need some advice. 

I have a core i5 system for which I recently bought 12G of RAM and a 1G Video card only to find that my Win 7 32-bit only supported the 3.5G max (doh! shoulda seen that coming). 

The obvious solution is to run Ubuntu 64bit, instead, so I can make use of the full capabilities.

I want to get a new HD and install Ubuntu on that. 

What would you advise in terms of a setup? Swap/Partitions, etc

Also, any 'gotchas' would I need to look out for? 

What I also want to do is to run my existing Win 7 as a Virtual Machine (VirtualBox, of course), since I need this for work. Will I be able to port my existing win7 install to a VBox VM? Any guides on this? 

Thanks
pvravi

---

### Post by kn0w-b1nary on 2011-04-14
Why don't you just install Ubuntu on the new HD, and point Grub to windows on the other drive?

---

### Post by bodhi.zazen on 2011-04-14
If it is for work, and work wants to use all that ram, have work buy 64 bit Windows :p

With that much RAM I doubt you will ever need swap, but it sort of depends on what you are wanting to do.

If it is a laptop you need a swap partition at least as large as RAM of hibernation / sleep.

The best way to run windows in a VM is to do a fresh install in the VM.

You can more easily go the other way, boot your Ubuntu install from windows. This is because a VM does not recognize you hardware, and windows is licensed by hardware, so it will complain when you boot it, then you would need hardware profiles.

If you have to ask how to do it, you will have to to a lot of reading and you risk trashing your windows install if you make a mistake.

---

### Post by idoitprone on 2011-04-14
[http://www.cyberciti.biz/tips/linux-swap-space.html](http://www.cyberciti.biz/tips/linux-swap-space.html)


for information regarding swap

---

### Post by pvravi on 2011-04-14
Thanks, people. 

No, 64-bit Win7 not an option. 

Also, I didn't want a dual boot - I've seen that I typically only boot one OS, never the other. 

As regards existing win7 on virtual box, I've tried that previously on VmWare, although with limited success. Any guides/info on this? I'm ready to read. 

Thanks
pvravi

---

