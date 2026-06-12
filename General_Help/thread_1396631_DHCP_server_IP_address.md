---
title: "DHCP server IP address"
date: 2010-02-02
forum: General Help
---

### Post by thor187 on 2010-02-02
I am not sure if it is possible, but I have a DHCP server (CentOS), I have just transfered from Windows XP, unfortunately my old IP in windows gave me internet access, now that I have installed Ubuntu it is a new IP and I do not have access. I would like to keep DHCP for when I go onto my home network I do not have to keep changing the settings from Static to DHCP.

Is this at all possible, or will I have to get someone to add my new IP on the server? Is there a way to tell my server to use my mac address and assign my old IP or something?

Thanks very much.

---

### Post by audiomick on 2010-02-02
Changing from windows to ubuntu shouldn't actually interfere.

Give us some more details of your setup. I gather the centOS server is the DHCP server. Is it also supplying the internet access? If not what is?

---

### Post by Iowan on 2010-02-02
Several (most?) DHCP servers have the option to assign a "static lease" based on MAC address. Once configured, your machine should receive the same address each time - but if/when you attach to a different network, it will get a new local address.

---

### Post by thor187 on 2010-02-03
Thank you for the replies. I am on the same network, and the CentOS server is the DHCP server and the internet server as well.

I am on a wired network at work, and a wireless at home, the home network has no server and is connected directly to the net. The wireless router is set up for DHCP at home.

I have no issues at home, just at work. I have a dual boot up, and when I boot into windows, my normal ip comes up and I have internet access, when I go into Ubuntu, it assigns a different ip address and I can not get access. The centOs server has squish loaded to only allow certain ip addresses to have internet access on the network.

I cant think of any other information off hand that may help.

Thanks again for the responses, most appreciated.

---

### Post by audiomick on 2010-02-03
Ok.
The suggestion that Iowan made sounds like the right thing in your case.
Maybe you need to talk to whoever administers the CentOS server.

Do you know what the MAC address is? Here is an  explanation
[http://en.wikipedia.org/wiki/MAC_address](http://en.wikipedia.org/wiki/MAC_address)
On some, but not all, routers with a DCHP server on them, you can tell the DCHP server that a particular MAC address must always get  a particular IP address. I think this is what you want. Whether you are in windows or Linux, the MAC address is always the same.
I don't know for sure that the function is available on the server you have, but I imagine that it would be.

---

### Post by thor187 on 2010-02-03
Thanks guys, I aksed the admin to assign my mac address on the centOs server and force it through, it worked. Am now in Ubuntu and online, you guys are legends, thanks again.

---

