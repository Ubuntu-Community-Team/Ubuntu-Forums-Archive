---
title: "Problem with wireless connection"
date: 2009-12-20
forum: General Help
---

### Post by mightyh on 2009-12-20
I installed Ubuntu Karmic in my computer but it does not recognize my wireless connection and I cannot connect to the internet. Can somebody help me with this problem. I have no problems connecting with my Windows XP but Ubuntu does not seem to have the proper driver for my wireless card.

---

### Post by hugmenot on 2009-12-20
Can you type this into terminal?

```
lspci | grep -i net
```

Paste the output.

---

### Post by FearfulJesuit on 2009-12-20
Also if you don't feel comfortable working with the command line, here's a GUI way, although less informative. 

Go to your system tab -> Administration -> Hardware Drivers and see if the wireless driver is installed. If it is not installed and you have the option of installing it then go ahead and install and restart. See if it works then.

---

