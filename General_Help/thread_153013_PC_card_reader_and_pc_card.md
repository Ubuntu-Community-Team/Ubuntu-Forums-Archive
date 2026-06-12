---
title: "PC card reader and pc card"
date: 2006-03-31
forum: General Help
---

### Post by razorblade on 2006-03-31
Hi all

I have just got my self Ubuntu linux. 
and I don't get my PC-card to work at all. 
trying to get my Wlan card to work. I have tryde [http://www.gidforums.com/t-4390.html](http://www.gidforums.com/t-4390.html)
but my computer does not react to my PC-card/pcmica card. 

do I need to activate my pc-card reader and how do I do that if I need to do it?

hope some one can help me. I have not use linux sense 98 and it i diffren today.

---

### Post by ranf on 2006-03-31
Umm, this thread is from 2004.

To see if the kernel recognizes the card you type this in a terminal:
```
tail -f /var/log/messages
```

and _then_ plug the card in.
What do you get?

---

