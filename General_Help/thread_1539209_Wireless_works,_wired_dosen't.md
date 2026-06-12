---
title: "Wireless works, wired dosen't"
date: 2010-07-26
forum: General Help
---

### Post by sebastianfaunes on 2010-07-26
Hi,
 
I am using Ubuntu 10.4 (netbook remix) on my netbook and have the wierdest problem. My wireless works great, but I can't even get the network manager to detect my wired connection.
 
I have the same problem everywhere, I can't manually configure it to work or with DHCP. Anyways, I can't rely on asking for all the config settings everywhere I go, especially if the person behind the desk barely knows how to turn on their PC. 
 
More info. I know the card works, before I had Ubuntu, it worked fine in Windows7
 
I had Ubuntu 9.10, same problem. Did a loopback test on 127.0.0.01 no problem 
 
Like I said, Wifi has no problem, problem is that I don't have Wifi access everywhere I go.
 
Best REgards,
 
Seb

---

### Post by prodigy_ on 2010-07-26
Run the following commands in terminal: ```
ip link show
ifconfig -a
```

Post the output here.

---

