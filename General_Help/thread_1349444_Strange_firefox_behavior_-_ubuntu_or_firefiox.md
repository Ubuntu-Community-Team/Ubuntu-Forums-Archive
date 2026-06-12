---
title: "Strange firefox behavior - ubuntu or firefiox?"
date: 2009-12-08
forum: General Help
---

### Post by jimstapleton on 2009-12-08
I have three machines, I'm not where the problem lies.

I'll start with my Ubuntu VM. I occasionally SSH to a FreeBSD box, and an RHEL box. None of the other two boxes can SSH back to the Ubuntu VM or to each other due to firewall/NAT settings.



If I SSH (-YCX) to the FreeBSD machine (prompt says sjss@elrond - elrond is the freebsd host), and open Firefox, it runs surprisingly fast. I go to an online IP checker, and I get the IP address of my ubuntu machine. I exit out, and have a prompt of sjss@ubuntu-vm (the ubuntu VM, strangely enough), and open firefox. I check the IP, and I get the same one as I did on the FreeBSD machine (they are at different physical locations, on different networks, no VPNs connecting them). I had previously noted similar behavior from the RHEL box.

Does anyone know what would cause this behavior? It's neat, but creepy, and if I want to download something on the remote boxes, I have to download it locally, and then ftp it over to the remote box. Also, sometimes, if I open firefox on the RHEL box first, then it will open on the RHEL box, rather than the ubuntu box, but until I close the RHEL instance, Firefox instances in ubuntu will also open on the RHEL box.

Oh, and this is Kubuntu, the version released in the past month or two.

---

