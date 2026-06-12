---
title: "The device eth0 is not ready"
date: 2010-11-01
forum: General Help
---

### Post by Chethan S on 2010-11-01
I have installed Ubuntu Lucid 64-bit. I configured my wired internet connection through pppoeconf as the default network manager appeared to be buggy as it did not allow me to browse some sites like linuxtoday.com. Now when I try to start firestarter, it actually detects the networks eth0, ppp0 and even shows data transferring but when I click upon start firewall it just says device eth0 not ready. I would also like to know how to start firestarter at startup without using password.

---

### Post by HiImTye on 2010-11-01
firestarter starts at startup in that it tells your kernel what to do (your firewall is actually built into your kernel, not some other program). the only functionality that is missing is the firewall log or whatever

I'm not sure if we're actually allowed to tell you how to bypass the root password anymore

---

