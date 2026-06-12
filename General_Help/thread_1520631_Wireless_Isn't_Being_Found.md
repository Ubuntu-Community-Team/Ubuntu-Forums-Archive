---
title: "Wireless Isn't Being Found"
date: 2010-06-29
forum: General Help
---

### Post by rws0005 on 2010-06-29
I just installed Ubuntu Netbook Remiix on my netbook (Lenovo S10-2) and everything went smoothly; however, I noticed that my wireless isn't picking up so I was wondering what steps I needed to take to fix that. 

Thanks,
rws0005

---

### Post by mikewhatever on 2010-06-30
Hook up an ethernet cable, then check under Sytem->Amin->Hardware-Drivers. In case there is nothing there, post the output of
lspci | grep -i network

---

