---
title: "Cant connect to ubuntu share from vista"
date: 2009-11-28
forum: General Help
---

### Post by jcl43 on 2009-11-28
Hi all. I have a share on my ubuntu box. I can see it in windows, but when I try and open it I get an error saying the network path was not found.

I have looked around and dont know much about samba, but Im guessing its perhaps something with my config? If anyone has experienced I would really appreciate the help!

Thanks in advance.

EDIT: Im running Ubuntu 9.10 and vista bu$iness

---

### Post by jamesisin on 2009-11-28
Can you get to the machine itself by using the run dialog (either [machinename] or [ip.adrs.of.mach])?

I am seeing trouble getting access to a Samba share in 9.10 when the guest access is turned on and the two machines are not in the same domain/workgroup.  I am able to access the share by requiring credentials (guest access off).

---

### Post by jcl43 on 2009-11-28
Got it figured out by following guide here

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by jamesisin on 2009-11-28
Ok.

---

