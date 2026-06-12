---
title: "transmission has no upload speed"
date: 2011-03-26
forum: General Help
---

### Post by bitbomb on 2011-03-26
I can download at a reasonable speed but I am getting no upload speed to other clients.  And I really mean NO UPLOAD, three torrents have 2 or less seeds and 80 peers and I still have no upload speed??  I have my transmission port properly forwarded in my router.  What else am I missing?

---

### Post by DanneStrat on 2011-03-26
> **bitbomb said:**
> I can download at a reasonable speed but I am getting no upload speed to other clients.  And I really mean NO UPLOAD, three torrents have 2 or less seeds and 80 peers and I still have no upload speed??  I have my transmission port properly forwarded in my router.  What else am I missing?

Do you use "gufw" for firewall management?

If so you may have a general rule to deny all

incoming traffic.

Have you also tried to go into transmission's

preferences and test if the port is forwarded

properly on the "network" tab?

---

### Post by bitbomb on 2011-03-26
The "test port" option in Transmission showed that he port was forwarded properly.  I did a port scan of my external ip using nmap and did not detect the port as open.  I restarted my router and did the scan and the port was open.  I think everything is okay now.  Thank you for the quick reply!

---

### Post by DanneStrat on 2011-03-26
> **bitbomb said:**
> The "test port" option in Transmission showed that he port was forwarded properly.  I did a port scan of my external ip using nmap and did not detect the port as open.  I restarted my router and did the scan and the port was open.  I think everything is okay now.  Thank you for the quick reply!

You're welcome!

---

### Post by newbuntuxx on 2011-03-26
Also, to check your ufw status run:

```
sudo ufw status
```

This will show you the firewall rules and status.

You can also enable logging and check if ufw is blocking traffic to certain ports. First enable logging:

```
sudo ufw logging on
```

The ufw logs are written to: /var/log/messages, so to view live logs, run:

```
tail -f /var/log/messages | grep UFW
```

To disable ufw run:

```
sudo ufw disable
```

---

