---
title: "VPN question"
date: 2011-03-09
forum: General Help
---

### Post by unbuntunewb on 2011-03-09
Hello,

I recently purchased a vpn service from [www.hostizzle.com](www.hostizzle.com) and have made a successful connection via KVpnc however I am quite confused. When I go to [www.whatismyipaddress.com](www.whatismyipaddress.com) it is the same IP I always had. I checked the FAQ on the site and it goes on about routing tables. This means nothing to me. Can someone explain to me in english what is going on? I thought I should have a new IP addresss. How do I test to see if my vpn is working? did i get scammed?

thanks for your input.

---

### Post by inkrypted on 2011-03-09
Routing tables are a list telling a service to use a certain port for instance internet browsers use ports 80 or 8080, e mail usually uses ports 25 and 110. It is possible that you need to run your VPN software as administrator so it can modify these ports correctly. To launch a program as administrator in Ubuntu use gksudo before the command and Kubuntu use kdesudo before the command.

---

### Post by inkrypted on 2011-03-09
VPN's usually have a trade off of privacy for speed. If you are doing this to stay secure while downloading you might check out moblock or iplist.

---

### Post by unbuntunewb on 2011-03-09
Turns out I didnt have the right permission, fixed that and now all is well.

Thank you.

---

