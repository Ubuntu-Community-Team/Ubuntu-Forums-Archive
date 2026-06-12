---
title: "Access Ubuntu Server VM on desktop"
date: 2012-01-29
forum: General Help
---

### Post by HoodedHooligan on 2012-01-29
I installed Ubuntu Server Addition on a Virtual Box with the goal of playing around with a LAMP server and SSH. I realized right after I installed it that I could not access the server on my desktop through the server's IP address (probably because its on a VM). There has to be a way to do this and Google isn't helping.

---

### Post by Cheesemill on 2012-01-29
In the VM options, make sure you have networking set to bridged mode so that you can access it from the host system.

When you have rebooted the Server VM you can use ifconfig to give you the address that needs to be used to connect to it.

---

