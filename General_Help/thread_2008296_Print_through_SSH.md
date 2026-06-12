---
title: "Print through SSH"
date: 2012-06-22
forum: General Help
---

### Post by rajtendulkar on 2012-06-22
Hello,

I want to print through SSH.
The configuration is such that I am able to access the HTTP URL of the printer.
```
HP_printer.mydomain.com
``` from the firefox browser. I can see the printer information in it. When I try to ping this domain or the IP address, I get a ICMP Message as Packet Filtered. 
So the router in between is printer and my computer is blocking the ICMP Packets. 
Thats why when I try to add a network printer, Ubuntu is not able to find it.

Suppose I login through SSH to a server which is on local network as printer, I am able to ping the printer.
I want to print directly from my laptop to this printer. Could anyone give me some solution?

I am using Ubuntu 11.10 and my printer is HP Color LaserJet CP2025dn.

Thanks,
Raj

---

### Post by LewisTM on 2012-06-22
First establish a ssh port forward that will bind the remote host's CUPS server to local port 6631.
```
ssh -fN -L 6631:localhost:631 user@host
```
Then add a new network printer using the address:
ipp://localhost:6631/printers/<printer name>
You can see what printers are available simply by browsing the address [http://localhost:6631/printers/](http://localhost:6631/printers/)

That's it! Now don't forget to establish the port forward whenever you need the printer (at login or later).

Cheers!

---

### Post by rajtendulkar on 2012-06-22
Thanks for the reply !

When do the SSH command I get the following error message - 
```
Cannot fork into background without a command to execute.
```So I removed -f option which gave me a console to login to the server.

---

### Post by LewisTM on 2012-06-22
> **rajtendulkar said:**
> Thanks for the reply !

When do the SSH command I get the following error message - 
```
Cannot fork into background without a command to execute.
```So I removed -f option which gave me a console to login to the server.
Sorry it should be -fN. That's if you want to just fork the process in the background, assuming you have setup a passwordless ssh login using keys.

---

### Post by rajtendulkar on 2012-06-22
Thanks... it works like charm ! :D

---

