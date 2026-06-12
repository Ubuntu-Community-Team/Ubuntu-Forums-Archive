---
title: "compiling and updating drivers"
date: 2010-01-23
forum: General Help
---

### Post by Cardale on 2010-01-23
I have a wifi card that has a generic driver through ubuntu that doesn't give it near the capabilities it has with another driver I found at another website.  I compiled this driver myself and installed it, but after an update all effects of that driver seem to be gone. 

My understanding of drivers and how they interact with Ubuntu is null, so I guess I was hoping some one could enlighten me as to what happened and how to make sure it doesn't happen again.

I guess another question would be why isn't Ubuntu using this driver as default?  If they need help finding out about these types of things what do I do?

---

### Post by lidex on 2010-01-23
What I know about wireless could fill a thimble but this link looks to be very comprehensive:
[https://help.ubuntu.com/community/NetworkDevices]("https://help.ubuntu.com/community/NetworkDevices")
If the driver is installed correctly, you may need to "blacklist" another driver that is taking control:
[http://ubuntuforums.org/showthread.php?t=1377788]("http://ubuntuforums.org/showthread.php?t=1377788")

---

### Post by lidex on 2010-01-23
> I compiled this driver myself and installed it, but after an update all effects of that driver seem to be gone. 
So this worked for you initially?

---

### Post by falconindy on 2010-01-23
If by update you mean kernel update, then this is expected behavior. Drivers are kernel specific, so you'll need to recompile for each new kernel install.

---

### Post by Cardale on 2010-01-24
> **falconindy said:**
> If by update you mean kernel update, then this is expected behavior. Drivers are kernel specific, so you'll need to recompile for each new kernel install.

Damn bummer.

---

### Post by Cardale on 2010-05-02
How would I go about automating this process?

Say for instance a update came out.  How would I have this information recompiled after a kernal change, or simply attempt to have the canonical team use it in their repositories instead of the other versions of the driver that are by far less than adequate?

---

