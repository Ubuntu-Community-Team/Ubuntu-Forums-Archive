---
title: "Setting up Tor."
date: 2010-01-11
forum: General Help
---

### Post by eeeguy on 2010-01-11
Hey, I need a idiot-proof tutorial on how to install, setup, and configure Tor. I need to use it for bypassing webfilters and such. Thanks in advance.:popcorn:

---

### Post by ankspo71 on 2010-01-11
Hi,
If this is for just websurfing, you can use one of many web based services too. Many of them don't affect speed either. Have a look at [http://www.proxy4free.com/](http://www.proxy4free.com/)
Hope this helps.

---

### Post by ankspo71 on 2010-01-11
Have you tried this one? 
[http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)

If not here is this one (tor with vidalia)
[http://onlyubuntu.blogspot.com/2008/03/howto-setup-vidalia-tor-gui-with-ubuntu.html](http://onlyubuntu.blogspot.com/2008/03/howto-setup-vidalia-tor-gui-with-ubuntu.html)

---

### Post by Project PWNED on 2010-01-11
Warning: Tor is not all that it seems. Yes, it bypasses certain filters/blocks, however there is incentive to run a Tor exit node, where the Tor network ends and the connection to the destination website is done.

For instance, with many of the SSL MITM attacks, you could specifically target SSL sites like email (Gmail, Hotmail, Yahoo) or social networking (Facebook, Myspace, etc) and read "encrypted" logins that you thought was encrypted through SSL/HTTPS.

There has been instances in the past where Tor exit node operators were "sniffing" exit node traffic, capturing emails, etc. for "research". There's too much incentive to do this, because I've noticed some funny things on Tor nodes.

I would personally go with a VPN or a VPS service, where you install a VPN for your personal usage, and you pay for the VPN/VPS with a prepaid credit card so you can stay "anonymous" online.

---

### Post by Ian Clark on 2010-01-15
> **Project PWNED said:**
> I would personally go with a VPN or a VPS service, where you install a VPN for your personal usage, and you pay for the VPN/VPS with a prepaid credit card so you can stay "anonymous" online.

VPN's are not anonymous because they are proprietary (though the risk might not be more than using TOR). Aside from bearing the cost, the buyer helps to create vested interests in Chinese censorship.

Has anyone heard where the Psiphon project went?

---

