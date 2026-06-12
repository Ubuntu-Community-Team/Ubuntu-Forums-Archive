---
title: "Internet not working"
date: 2011-05-10
forum: General Help
---

### Post by ihaveaname on 2011-05-10
Hey guys,

Just then I tried to use Skype and Firefox and they just wouldn't work. Thing is though, it's a wired connection and when I plug it into my other computer it works perfectly fine. Any ideas on what's gone wrong? Just beforehand I'd tried to connect an external monitor to this computer (laptop); that's the only thing that I can think of that could have stopped the internet working, but I can't imagine how.

I run ubuntu 10.10 netbook edition.

Any ideas on how to fix this? I need it to Skype my mum :(

---

### Post by enimeizoo on 2011-05-10
Hello,
You can try these commands
```
 
sudo ifconfig eth0
sudo dhclient eth0

```I'm not sure the sudos are necessary, thought. 

If it doesn't work, you can send the output of ifconfig.

---

