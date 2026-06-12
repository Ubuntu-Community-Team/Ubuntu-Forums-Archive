---
title: "Customized Dual boot Dell 1525 Ubuntu/Vista Ultimate Windows - Re-install Prep?"
date: 2009-10-02
forum: General Help
---

### Post by Varenne on 2009-10-02
About to do a total reinstall of Windows Vista Ultimate and was wondering if I need to backup anything Ubuntu (9.04) related first? 

Windows is or seems to be slightly corrupted. Missing shortcut icons, missing Start menu folders like Accessories, although it says they are there, odd behaviors in programs like Firefox, etc. and after numerous attempts to repair it all I'm just done with it. Time to just install a fresh copy and start over IMO (And start using Ubuntu more for everything!)

Boots via standard Grub dual-boot setup; always Ubuntu as first choice, Windows last, which is they way I like it. 

Custom drive partitioning, Windows on the old C:/ partition, Windows Restore partition deleted, waste of drive space IMO. Small FAT partition for Dell Media nonsense still in place.

Any pointers?

Thanx in advance!

---

### Post by linux4life88 on 2009-10-02
You could install something like Virtualbox and run Windows as a virtual machine instead of dual booting. I would only do this though if you plan on using Ubuntu the majority of the time. This is just simply another option available to you.

---

### Post by Varenne on 2009-10-02
You know, that's not  a bad idea and thanx for the reply!

And yes I broke my addiction to Windows a while ago, now that I have Ubuntu I run that 90% and Windows about 10%. Unfortunately I still need access to the MS Office+Visio applications, Open Office still doesn't quite cut it.

I had tried a number of virtualization implementations to run Windows on; VMware, Xen, etc. and wasn't really that impressed with app speed.

Think I'll leave the old Windows Vista install in place and give VirtualBox a go. If it works out I can always blow that partition away later.

---

### Post by linux4life88 on 2009-10-03
Virtualbox is what I use. If you want USB support then download the Personal Use and Evaluation (PUEL) version (that is if you are just using this for personal use and not for business use) and not the Open Source Edition (OSE). Here is the link:

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Virtualbox has just always been what I've used and I've never had any problems with it. It has always worked fine for me. Hope everything works out.

---

### Post by Varenne on 2009-10-03
Yup, strictly personal use. I found the OSE package via Synaptic easy enough, think I'll test drive that version first, maybe go for the PUEL version later. I do use all WD USB drives now for file storage, backups, etc. so it'd be a good idea I think.

Also found a very short blurb on VirtualBox in The Official Ubuntu Book, but I think I'll pick up the server edition next as that is my goal for this new personal Ubuntu learning lab I've built.

Thanx again for the input

---

