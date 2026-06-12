---
title: "Problem with Remmina,KRDC,RDview and RD in General"
date: 2012-03-08
forum: General Help
---

### Post by saintslaughter on 2012-03-08
I'm trying to connect via RDP to my work using my ubuntu box. I HAVE to use RDP, I Can not use VNC. I can connect to both servers win2ks and win2k8s with a windows machine, but I would prefer to do it from my ubuntu box. It is not a firewall issue on either end, nor a settings issue as far as name/password/domain/server/port. I have tried 3 different applications, and I get the same results with all 3. The client appears to connect, and then totaly crashes and closes out on me. I never see the remote computers desktop.  I am running Ubuntu 11.10.

---

### Post by dcstar on 2012-03-09
> **saintslaughter said:**
> I'm trying to connect via RDP to my work using my ubuntu box. I HAVE to use RDP, I Can not use VNC. I can connect to both servers win2ks and win2k8s with a windows machine, but I would prefer to do it from my ubuntu box. It is not a firewall issue on either end, nor a settings issue as far as name/password/domain/server/port. I have tried 3 different applications, and I get the same results with all 3. The client appears to connect, and then totaly crashes and closes out on me. I never see the remote computers desktop.  I am running Ubuntu 11.10.

The latest Remmina package fixed an issue like this, I don't know if it has made it to the official repositories yet.

Do a search on directly installing it from a PPA. Remmina 0.9.3 works fine for me.

---

### Post by saintslaughter on 2012-03-09
> **dcstar said:**
> The latest Remmina package fixed an issue like this, I don't know if it has made it to the official repositories yet.

Do a search on directly installing it from a PPA. Remmina 0.9.3 works fine for me.

Thank you I will give this a try.

---

### Post by saintslaughter on 2012-03-09
Update:: I'm using 0.9.3-2 of remmina. on 64 bit. So far all I can find is 1.0.0 for i386

---

