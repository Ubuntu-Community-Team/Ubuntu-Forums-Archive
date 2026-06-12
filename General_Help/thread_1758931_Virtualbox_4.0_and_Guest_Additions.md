---
title: "Virtualbox 4.0 and Guest Additions"
date: 2011-05-15
forum: General Help
---

### Post by Condor Cluster on 2011-05-15
Just installed Virtualbox 4.0 on my netbook. Cannot seem to find an option for guest additions though.

How do I install guest additions on Virtualbox? (don't think I have the OSE version)

Thanks

---

### Post by rigel4 on 2011-05-15
If you have the guest additions downloaded, all you have to do is
right the click the file and click open with virtual box.
Then open your virtual machine and Install.

That's all I do and works for me.

---

### Post by Condor Cluster on 2011-05-15
Think I figured it out now...

Once I loaded Windows XP, I found an option under Devices menu to install Guest Additions.

When I clicked on it, a window popped up from within XP, and it installed guest additions in XP.

Kinda weird, as I though it would install under Ubuntu since that is the host...

---

### Post by An Sanct on 2011-05-15
The host needs no guest additions, the guest does (hence, the name)

If there are not guest additions present, you can click Devices -> Install guest additions in VirtualBox and it will download and mount the ISO.

---

