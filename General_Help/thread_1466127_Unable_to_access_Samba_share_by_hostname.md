---
title: "Unable to access Samba share by hostname"
date: 2010-04-30
forum: General Help
---

### Post by CharlesA on 2010-04-30
I got my server set up with 10.04, and with everything installed: DHCP, SSH, Samba, VBox, etc.

DHCP, SSH work fine, but I am having problems where I cannot ping the hostname of the machine.

It worked for a few minutes after I got everything installed and now it's not letting me connect via hostname. **I can connect fine if I use the IP address.** I cannot ping the machine by hostname unless I add it's IP address to the hosts file.

Any suggestions on this?

---

### Post by lijcam on 2010-04-30
Issue is not with samba. You if you cannot ping via host name its a DNS problem. Have you configured DNS on the server?

---

### Post by CharlesA on 2010-04-30
No DNS on this server. It's strange, since it works fine with 9.10, but I think that might be due to having the hostname look like this on 9.10:

"thor.sd.cox.net"

instead of just "thor" (on 10.04).

I guess I should go ahead and install a DNS server and see what happens.

---

### Post by lijcam on 2010-04-30
What are you using for dhcp? I ask as you could have a look at dnsmasq as it is light weight and provides dhcp and dns. Its designed for small network. I'm not sure if it has a gui but its config file is quite simple to work with.

---

### Post by CharlesA on 2010-04-30
I'm currently using dhcp3-server for DHCP. Mostly since I can configure it in Webmin.

---

### Post by HereInOz on 2010-04-30
If you are using Windows to access the samba share, try putting the hostname and the IP address of the server into the hosts file of your Windows machine.  

The hosts file is in \Windows\System32\drivers\etc\

Sort of like a poor man's DNS record.  Use notepad to edit it following the examples.

---

### Post by lijcam on 2010-04-30
I've never used webadmin but had a quick look at their homepage and see that it does dns. I'd reckon that it should be fairly simple to active it with its gui.

---

### Post by CharlesA on 2010-04-30
Thanks guys.

I think I've got it working now. Had to set up BIND, create a master zone and add host records for it.

Seems to be working now. :)

EDIT: Is it possible to set it up so that I can ping using just the hostname without including the DNS suffix?

Example:

```
ping thor
```

Instead of:

```
ping thor.local
```

EDIT: I had to set the DHCP server to assign a domain name to the clients. Works fine now. :)

---

