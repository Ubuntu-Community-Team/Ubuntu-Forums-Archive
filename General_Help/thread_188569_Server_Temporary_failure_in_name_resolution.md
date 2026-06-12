---
title: "Server: Temporary failure in name resolution"
date: 2006-06-04
forum: General Help
---

### Post by Dagur on 2006-06-04
I'm having problems with my small server. I used to run 5.10 and upgraded to 6.06 just recently. Everything worked fine but now I keep getting this error (for example with wget):
```

dagur@server:~$ wget mbl.is
--11:15:16--  http://mbl.is/
           => `index.html.1'
Resolving mbl.is... failed: Temporary failure in name resolution.

```

And I can't seem to be able to ping anything, not even local IPs (even the one i'm ssh-ing from). I tried purging resolvconf as suggested in another thread but it didn't do anything for me.

---

### Post by adwait on 2006-06-04
Is your ethernet card properly configured? Have you set it up for static IP or for Dynamic Ip? Does that setting match with the one in your router?

---

### Post by Dagur on 2006-06-04
I can only guess that it's properly configured. Apache and FTP works and can be accessed form the internet. It's set up for static IP and the router seems to direct traffic to it correctly.

---

### Post by Dagur on 2006-06-05
Problem solved!

I had to put my ISP's nameservers in /etc/resolv.conf

like so:

nameserver 85.197.192.20
nameserver 85.197.192.21

---

### Post by Dagur on 2006-07-02
/etc/resolv.conf is deleted when I reboot, making the problem come again. Why? :-(

---

### Post by quixote on 2006-07-07
I'm having nameserver problems, and am trying to figure them out.  I saw this on another forum (don't remember where, unfortunately) posted by "elocal":

"Keep in mind that /etc/resolv.conf gets overwritten every time you run a dhcp client, so either use static IP, or prevent your dhcp client from overwriting /etc/resolv.conf (check its respective manpage)."

So, in my case, once I figure out what my "dhcp client" is, I'll be all set....;)

---

