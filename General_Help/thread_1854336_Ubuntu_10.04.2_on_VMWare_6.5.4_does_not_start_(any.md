---
title: "Ubuntu 10.04.2 on VMWare 6.5.4 does not start (any more)"
date: 2011-10-04
forum: General Help
---

### Post by Stephan Wöbbeking on 2011-10-04
Hi,

I am pretty new to Ubuntu - hopefully the result is, that my problem is quite an easy one...

I have an Ubuntu 10.04.2 installation of a VMWare instance (6.5.4) which was working ok for a few weeks already. Recently I switched on a serial port and I think I tried to update the VMWare tools which both I think it's not the reason for the problem but I don't really know.
The point is, that my Ubuntu does not start (completely) any more - I didn't really see a good reason what could have made Ubuntu to resign. I do see the logo screen with "the running bubbles" (Is that known as the "splash" screen?) but it will go forever. When I press Esc, the attached output appears. I can change to the consoles via Alt-F1 to F6, but whatever I checked locked fine to me.
How can I find out what is missing, what holds Ubuntu back from starting my desktop (I already tried "sudo init 6" and "startx" just by chance, didn't help)?

Thanks for any ideas,
Stephan

---

### Post by Stephan Wöbbeking on 2011-10-05
Noone any idea about it? Or is it so obvious, that I must feel ashame having posted it?

---

### Post by Dangertux on 2011-10-05
First off welcome to the forums, and no you should not feel ashamed of any question :-)

Secondly, if you install VMWare tools it will often times (read most of the time) install an alternate X server. I have had issues with the latest VMware tools and Ubuntu.

What sometimes helps is dropping to a console and doing the following

```

sudo dpkg-reconfigure xserver-xorg

```

Keep in mind your Xserver will not support the resolution supported by the vmware tools x server but it should restore a working desktop environment.

Hope that helps.

---

### Post by dcstar on 2011-10-06
> **Stephan Wöbbeking said:**
> Noone any idea about it? Or is it so obvious, that I must feel ashame having posted it?

Why not ask in the Virtualization forum where **all** the VM issues are?

---

### Post by Stephan Wöbbeking on 2011-10-24
Hi, sorry for the late reply (I had to help introducing our new family member to the world ;) ) and thanks for the answers.

I have tried the xserver configuration suggested from Dangertux but it didn't help at all. Moreover the system behavior didn't change at all.

Regarding placing this issue to the virtualization section; well, I agree as I have been thinking about it for quite a while before posting, but I wasn't sure (and still not) if this is really helping. I don't know if this issue is related to the VMWare I am using nor if the solution will relay somehow on knowledge about the virtualization. Do you have any information about this behavior, do you think IT IS related to the virtualization system?

Thanks,
Stephan

---

