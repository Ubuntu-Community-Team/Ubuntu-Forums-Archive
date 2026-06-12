---
title: "Free VPS solutions?"
date: 2011-09-21
forum: General Help
---

### Post by Colo2 on 2011-09-21
Hello :)

I need to know if anyone knows of any good VPS solution that are free?

I mean, software that allows you to run virtual PCs within the actual PC itself, like virtualbox. Thing is: there will be no GUI, headless and the whole thing linux.

Thanks :)

Tom

---

### Post by dcstar on 2011-09-22
> **Colo2 said:**
> Hello :)

I need to know if anyone knows of any good VPS solution that are free?

I mean, software that allows you to run virtual PCs within the actual PC itself, like virtualbox. Thing is: there will be no GUI, headless and the whole thing linux.

Thanks :)

Tom

What is not "free" about the multitude of VM platforms already available for Ubuntu?

---

### Post by cryptotheslow on 2011-09-23
Maybe Xen Hypervisor is the kind of thing you are looking for?
[http://xen.org/products/xenhyp.html](http://xen.org/products/xenhyp.html)

---

### Post by patryk77 on 2011-09-23
I use QEmu, you can read the Virtualization section of the server guide:

[https://help.ubuntu.com/10.04/serverguide/C/virtualization.html](https://help.ubuntu.com/10.04/serverguide/C/virtualization.html)

For other versions of Ubuntu:
[http://www.ubuntu.com/business/server/technical-resources](http://www.ubuntu.com/business/server/technical-resources)

Libvirt is awesome (and based on qemu), so read that section first.

It even supports Windows:
[http://glog.procrasstination.com/index.php?/archives/20-Howto-Install-Windows-XP-in-QEMUKVM-on-an-Ubuntu-Server.html](http://glog.procrasstination.com/index.php?/archives/20-Howto-Install-Windows-XP-in-QEMUKVM-on-an-Ubuntu-Server.html)

---

### Post by LumbeeNDN on 2011-10-04
@colo, hope u don't mind me hi-jacking your thread ):P

...I am a sys admin @ a tech college, and some of our instructors have asked for help in offering servers to their students, and I am looking at Xen. So we would have anywhere from 50-100 students with a server for each student. So this is just a matter of hardware. If I want 10gb servers do I just multiply 10gb by the number of servers I want (plus some space for the base server) to figure how much total hard drive space I will need?

My other question is on authorization. My goal would be for the schools IT staff to only maintain the server, but allow instructors to login to the server and have the ability to create/destroy virtual servers for their students. Is this possible out of the box?

Any info appreciated....thanx!

---

