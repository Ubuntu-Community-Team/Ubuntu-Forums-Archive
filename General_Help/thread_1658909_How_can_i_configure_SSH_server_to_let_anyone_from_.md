---
title: "How can i configure SSH server to let anyone from outside LAN connect"
date: 2011-01-03
forum: General Help
---

### Post by Mori_7 on 2011-01-03
Hello folks 

I tried yesterday with my friend to create ssh server in ubuntu server via vmware on his pc and we're done it, but after typed this (sudo apt-get install openssh-server ) we don't knows what we supposed to do after that, i google it many times but i couldn't find any what i need, all those guides talks about how to connect on ssh in LAN or by useing 192.168.xx.xx but i need to make connect from outside his network, is that mean he need something like domain name or **DynDNS **?, my friend got daynamic ip from his isp and i've seen before many websites offers secure shell able to made it connect, please anyone can help me to clear that

---

### Post by seawolf167 on 2011-01-03
After you setup the ssh server, you should forward the ssh ports to your computer from your gateway (ssh uses port 22).

Then, you'll need to know the external IP address of the lan network you want to access ([http://www.whatismyip.com](http://www.whatismyip.com))

When you connect from a remote machine, you'll use the command

```
ssh -l your_username your_ip_address
```

Your machine will then prompt you for your password, which once you enter gives you user access.

If you have a dynamic ip address or don't want to remember your ip address or pay for a domain name, I suggest the free service NoIP ([http://www.no-ip.com/](http://www.no-ip.com/)), where you can use the program [noip2 ]("http://www.no-ip.com/downloads.php?page=linux")to automatically update your dns/ip info.

---

