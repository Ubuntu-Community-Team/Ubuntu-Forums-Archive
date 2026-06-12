---
title: "How many open ports should I have?"
date: 2010-06-26
forum: General Help
---

### Post by blur xc on 2010-06-26
I'm trying to figure out why I have so much idle network traffic.  I got tcpdump to display my network traffic, but I don't know how to decipher the information, at least not yet...

So, I opened up my network tools dialog and did a port scan for my router's ip address (don't know if that's the right thing to do or not) an it appears that I have 8 open ports...

What I would really love to know, is what program on my computer is sending and receiving data from the internet.

thanks,
BM

---

### Post by Rubi1200 on 2010-06-26
From the terminal:

```
sudo netstat -tulnp
```

or ```
sudo lsof -i -n -P
```

Both provide information about what is going on.

By default, Ubuntu does not ship with open ports, so if you see anything other than the cups printing service listening or services you specifically started you should investigate further.

---

