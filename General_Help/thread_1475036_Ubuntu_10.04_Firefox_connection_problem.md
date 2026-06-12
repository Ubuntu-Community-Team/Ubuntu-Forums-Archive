---
title: "Ubuntu 10.04 Firefox connection problem"
date: 2010-05-06
forum: General Help
---

### Post by Revoc on 2010-05-06
I recently installed Ubuntu 10.04. Everything seems to operate OK except Firefox has significant problems connecting to websites. It often (usually) times out while trying to load pages. The message I get is either "The connection has timed out" or "Problem loading page".
I previously had Ubuntu 9.04 installed and Firefox worked fine on it. I installed Konquerer browser and it works just fine. I have no trouble with other connections such as updating or downloading new software for ubuntu.  So, my guess is the problem is confined to Firefox. I've tried reinstalling it, and the problem is still there. 
Any suggestions would be much appreciated

---

### Post by gonk on 2010-05-07
I had a similar problem.  Updates and Chromium browser works, but Firefox doesn't.

This fixed it for me:

[http://www.craigmayhew.com/blog/2009/11/slow-dns-lookups-in-firefox-on-ubuntu-9-10-karmic-koala/](http://www.craigmayhew.com/blog/2009/11/slow-dns-lookups-in-firefox-on-ubuntu-9-10-karmic-koala/)

Even though this was written for 9.10, it also works on 10.04.

---

### Post by Revoc on 2010-05-07
Thanks gonk!

That seems to have fixed the problem. It seems strange that this apparently isn't troubling most folks that have gone to 10.04.

Again, thanks for taking the time and effort to help!

Revoc

---

### Post by gonk on 2010-05-07
Update: Although this fixed Firefox for me, there were other programs that still had problems resolving DNS.  E.g. when Software Centre or Synaptic ran the flash-installer (which runs a script to download flash), the DNS resolve failed (it resolved to 1.0.0.0) and therefore flash didn't install properly.  It also had the same problem when downloading mscorefonts.

The problem is apparently due to my modem/router not handling IPv6 DNS resolving properly.  This explains why the problem isn't more widespread -- i.e. most people use modem/routers that handle the DNS resolving properly.  You may want to investigate updating your modem/router firmware (unfortunately it's not an option for me).

I've tried several computers with Ubuntu 10.04 at home and they all have the same problem.  However if I run Fedora 12, 13beta, Windows XP, Vista, 7 they work fine.  But if I run Ubuntu 10.04 at work, it works fine.  Therefore it seems to be a compatibility problem with Ubuntu and my home router.

Anyway, I've found a better system-wide way to fix this.  Give your computer a static IP address and use the DNS servers of your ISP.  This bypasses the router's DNS resolving, and the computer queries the ISP's DNS servers directly.  Everything works when I do this.  Let me know if you need help with this step.

---

### Post by todb on 2010-05-18
For what it's worth, I don't believe IPv6 is to blame. I'm running wireshark, and I'm not seeing any IPv6 DNS requests originating from my workstation --- after disabling IPv6 for Firefox (about:config, then network.dns.disableIPv6 => false), the problem persists.

I do strongly suspect my router is to blame; it's new and purports to support IPv6, but it's a shame that Firefox is so susceptible to this problem.

Once I get to a reboot point, I'll try the modprobe route of disabling IPv6 completely, but I'm still skeptical.

---

