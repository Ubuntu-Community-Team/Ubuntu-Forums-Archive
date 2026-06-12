---
title: "terminal command help"
date: 2009-12-06
forum: General Help
---

### Post by spiky001 on 2009-12-06
Hi i am looking for the terminal command i can use to restart just the wired connection ethO i can restart network manager but need to restart ethernet only while leaving internet still connected hope someone can help?

---

### Post by spiky001 on 2009-12-06
i hope ther is some one with an ans

---

### Post by blazemore on 2009-12-06
What about
```
sudo ifdown eth0 && sudo ifup eth0
```

From here:
[http://en.kioskea.net/faq/sujet-1141-linux-restarting-the-network-interface-using-command-lines](http://en.kioskea.net/faq/sujet-1141-linux-restarting-the-network-interface-using-command-lines)

---

### Post by spiky001 on 2009-12-06
Hi blaze tried what u said i get a return interface ethO not configuered any help with that plz

---

### Post by pbrane on 2009-12-06
That's eth0 (number zero), you typed an O (letter o) in your post.

---

### Post by spiky001 on 2009-12-06
hi have tried that as well still get same reply not configuered. I need to do this so i can reset the server connection to network via remote access

---

### Post by pbrane on 2009-12-06
Are you using Network-Manager? auto-eth0 should be configured by default if your ethernet interface is okay. Are you able to use eth0 at all?

---

### Post by blazemore on 2009-12-06
Make sure it's zero, not the letter "O"!

---

### Post by amturnip on 2009-12-06
"network-manager" is nice for personally-attended connections, especially come-and-go wireless, but its predecessor, "networking", is nice for unattended, no-surprises connections.  

Judging by a look at /etc/init.d, both mechanisms appear to both be present in Ubuntu 9.10.  

Perhaps you could tell network-manager not to manage eth0; configure eth0 with "networking"; and then use "networking"'s relatively mature and robust command line interface, e.g. ifup and ifdown, to control eth0.

---

### Post by spiky001 on 2009-12-07
hi ppl I have solved problem many thanks to all, command i used is  sudo ifconfig eth0 down && sudo ifconfig eth0 up. but u put me in the right dirrection thanks again

---

### Post by blazemore on 2009-12-07
Please mark as Solved using the Thread Tools at the top of the page

---

