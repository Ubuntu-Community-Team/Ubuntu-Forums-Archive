---
title: "libvirt-bin auto start"
date: 2010-07-20
forum: General Help
---

### Post by siuchi on 2010-07-20
Hi all,

I have ubuntu 10.04 64bit server install.
I have install kvm and libvirt, but libvirt-bin does not start up automaticly when then server boot-up.

Can someone teach me how to make libvirt-bin startup automaticly.

Many Thanks

---

### Post by rubylaser on 2010-07-20
That's strange, libvirt-bin should definately be part of the startup scripts.  Can you see if you have a file in /etc/init.d/ called libvirt-bin ?

---

### Post by siuchi on 2010-07-21
Yes. The problem is solved. That is because there's another program which use up to 100%cpu and make libvirt-bin take 10mins to properly boot up. The problem is solved by removing the malfunction program.

thanks.

---

