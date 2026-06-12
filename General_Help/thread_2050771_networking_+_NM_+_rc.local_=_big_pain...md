---
title: "networking + NM + rc.local = big pain.."
date: 2012-08-31
forum: General Help
---

### Post by fabietto0102 on 2012-08-31
Hi, I've a very similar issue to [http://ubuntuforums.org/showthread.php?t=2042409](http://ubuntuforums.org/showthread.php?t=2042409) and hope you can help me please! 

I need to run 

```
sudo etc/init.d/networking restart
```

automatically at login, but how? 

I tried to add the line to rc.local but it doesn't work. From reading the thread, I suspect that I first need to be connected to the network, which I do using NetworkManager with a wifi connection. 

How can I write a while loop in shell that says "while I'm not connected, loop' please? I think of putting it in rc.local and hoping it lasts after I login..

---

