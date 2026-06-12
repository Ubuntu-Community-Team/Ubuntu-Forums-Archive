---
title: "Networking problem"
date: 2006-06-02
forum: General Help
---

### Post by sanderjd on 2006-06-02
I have posted this a couple times now without anybody responding to me and I can't find any information on the Wiki that seems helpful. I'm thinking next time maybe I'll post with a title like "Ubuntu sucks" because all of those posts, which rag on Ubuntu in the title and have a body that says there is a problem but can't or won't name it and seem to celebrate their own ignorance get lots of responses. 

Anyway, I won't actually do that but I'm getting pretty frustrated. y problem is simple. My DNS is set incorrectly by DHCP because of a crappy router I believe. This is OK, because I can set it manually to make it work. But everytime I restart, the settings are changed again. Is there some way that I can turn off DHCP for just my DNS settings but keep it on for everything else? Or can I lock the file with the DNS server addresses in it and keep it from being modified. Or do I just need to write a script that runs at startup that replaces the incorrect file with a modified one. Any ideas?

---

### Post by linuchsan on 2006-06-02
edit dhclient.conf, uncomment the line supersede, then between the quotes you can put your dns

---

### Post by Skye on 2006-06-02
To clarify what linuchsan said, edit /etc/dhcp3/dhclient.conf:
```
sudo gedit /etc/dhcp3/dhclient.conf
```
Then find the line called: **#supersede domain-name "fugue.com home.vix.com";** and edit it so that it reads: **supersede domain-name "yourDNSserver";**  Save it, close gedit, and restart, and you should be good.

---

