---
title: "preventing dnsmasq startup"
date: 2010-02-27
forum: General Help
---

### Post by fmigpaulo on 2010-02-27
I wonder how i can prevent the dnsmasq service domain to start when the system boots. I'm a home user and only use my machine to surf the Internet or write documents. My home network consists of a router (connected to an ISP) and computers on the network 192.168.1.0/24
By disabling the service, will i be able to navigate on web normally?
My problem is that this service is opening port 53 which i believe not be necessary for my requirements.

Thank you all in advance.

---

### Post by hwttdz on 2010-02-28
Perhaps this is a good place to start: [http://www.ubuntu-unleashed.com/2007/09/i-personally-like-gui-tools-but-i-also.html](http://www.ubuntu-unleashed.com/2007/09/i-personally-like-gui-tools-but-i-also.html) , you can remove it from all runlevels.  Then you're also going to want to change your network setup so it doesn't use 127.0.0.1 as a dns server.  But I might ask why you're disabling dnsmasq, I just enabled it myself a few days ago and I find it fantastic.  If you're sure you don't want it at all you could just remove/purge.

---

### Post by fmigpaulo on 2010-02-28
Thank you for responding so quickly and accurately.
After install and run bum (it was the first i've tryed):

```
sudo apt-get install bum
sudo bum
```
i managed to locate and prevent the service ran on startup.

As i'm not sure need to run the service in the future (perhaps to share the internet connection), so, i will not uninstall it.

Thank you very much.

---

