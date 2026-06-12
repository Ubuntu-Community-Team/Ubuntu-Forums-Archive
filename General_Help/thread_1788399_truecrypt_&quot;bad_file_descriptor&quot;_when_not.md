---
title: "truecrypt &quot;bad file descriptor&quot; when not connected to Internet"
date: 2011-06-22
forum: General Help
---

### Post by mvampire on 2011-06-22
So my truecrypt can't mount an encrypted partition when I'm not connected to the Internet.
It says "bad file descriptor"

When I connect - all is fine.

In wireshark I do not see any traffic at this time except "DNS standardquery AAAA <my laptop's name>".

What I mean under connect/disconnect:
I live in dormitory and connect to the Internet through my WiFi router, which has an Internet IP-address. However, to use Internet connection I need to open an ssh connection to some external server. Internet will work while this connection is up.

Any ideas?

---

### Post by kdford on 2012-01-18
Did you ever get an answer to this?  It is a problem as I might not have Internet connection while I travel.

Imported public key and signed it but that didn't make a difference.

---

### Post by pbulteel on 2012-03-08
The way to get this to work is to make sure that your hostname is in the /etc/hosts file. Usually it's also associated with the localhost ip address (127.0.0.1)

My entry looks like this.

```

127.0.0.1    mydesktop    localhost.localdomain    localhost
::1    mydesktop    localhost6.localdomain6    localhost6

```This should avoid the problem especially if you're not on a network. If you are on the network, this problem could happen if DNS is slow to respond.

-P

---

