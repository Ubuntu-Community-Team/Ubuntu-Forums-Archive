---
title: "Error code 10060: connection timeout"
date: 2011-12-20
forum: General Help
---

### Post by gacy on 2011-12-20
Dear all
I have recently installed LAMP on ubuntu 11.10 and I created a website (actually it is an installation of Wordpress) . I can "see" the website within our company network, but when I try to access it from any other place (i.e. from home) I get an error message: connection timeout.

Any idea what went wrong?
Thank you all!

---

### Post by fansaty on 2011-12-20
You're configured on your modem? Config modem to point to your web server.

---

### Post by gacy on 2011-12-20
> **fansaty said:**
> You're configured on your modem? Config modem to point to your web server.
What do you mean by modem? Is it the firewall?

---

### Post by fansaty on 2011-12-20
You're using a line internet <-> a modem <-> firewall <-> your LAN? Or thing else?

---

### Post by gacy on 2011-12-20
We have a LAN and it is behind a firewall.
I configured the DNS server to point the website-name to the ip address of the ubuntu machine. I haven't done anything with the firewall, though.

---

### Post by lisati on 2011-12-20
To make your web page accessible by the public, a good starting place is to configure your router to forward port 80 to your server. Your router is the box which all the computers plug in to.

---

### Post by fansaty on 2011-12-20
and you also try to create rules on firewall in order to allow ports which your web server is running on.

---

### Post by gacy on 2011-12-20
OK thank you!

---

### Post by gacy on 2011-12-20
Thank you. I will do that!

---

