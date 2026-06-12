---
title: "SOCKS Proxy on Router"
date: 2011-08-13
forum: General Help
---

### Post by ctult on 2011-08-13
Hello,

I am making a content filter for a school.  I have a computer with Ubuntu Server and the SOCKS proxy, a DD-WRT router, and a switch.  I was wondering how I could forward all requests through the SOCKS proxy before sending it to the Internet.

Could someone please help me?

--Sam

---

### Post by crook17 on 2011-08-14
you need to set up a dhcp server on the ubuntu box and set the gateway to the server, so when a client computer gets a ip it gets the default gateway that forwards dns etc etc. 

On another note i would recommend squid so you could sync it with ldap.

---

