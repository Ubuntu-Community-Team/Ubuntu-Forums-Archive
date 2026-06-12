---
title: "Setting DNS servers via command line?"
date: 2006-04-06
forum: General Help
---

### Post by Bonkerz on 2006-04-06
I just installed linux-wlan-ng and got my wireless to work, but it takes me forever to find a server because the DNS is set to my wireless router, instead of the DNS servers specified on the router. I tried changing them via Networking window, but then my wireless goes down and i have to reconfigure it. So how can i configure primary and secondary DNS via terminal?

---

### Post by ssalman on 2006-04-06
all you need is to edit your /etc/resolv.conf

I used to do:
```
sudo echo "nameserver 192.168.2.1" > /etc/resolv.conf
```

don't forget to check your gateway, I had a hell of time figuring out why my DNS setup did not work, while the gateway was not setup correctly (you set it up using "route" command)

hope this helps.

---

