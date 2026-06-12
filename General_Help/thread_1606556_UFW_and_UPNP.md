---
title: "UFW and UPNP"
date: 2010-10-26
forum: General Help
---

### Post by pmalvr on 2010-10-26
It seems that with ufw enabled It is impossible for upnp aplications to negociate with the network router the ports they need to be opened. Is there any way to make ufw and upnp work together?

Thanks

---

### Post by lovinglinux on 2010-10-26
If I remember correctly, you need to allow port 1900 between the machine and the router to make UPnP work. I don't use UFW, but there is probably an option to allow local network.

---

### Post by pmalvr on 2010-10-26
I already did that, but with no luck. Any other option??

---

### Post by lovinglinux on 2010-10-26
Monitor what is getting blocked when you use an UPnP enabled software:

```
tail -f /var/log/messages
```

---

### Post by pmalvr on 2010-10-27
I did that and It logs some few lines telling that the source port (from the router) is port 1900 and the destination port (to the computer) is another one, that by the way, changes every time I start the application. So I think for now the UFW firewall is not compatible with UPNP.

---

### Post by lovinglinux on 2010-10-27
> **pmalvr said:**
> I did that and It logs some few lines telling that the source port (from the router) is port 1900 and the destination port (to the computer) is another one, that by the way, changes every time I start the application. So I think for now the UFW firewall is not compatible with UPNP.

Enable incoming from the router to port 1900.

---

### Post by cocoa117 on 2011-02-12
I found the trick, on my firewall log it showed the you need to enable the firewall incomeing from 1900 to 1901, so 
sudo ufw allow proto udp from 192.168.0.0/24 port 1900 to any port 1901

worked for me.

---

