---
title: "How do I know my computer specs using the terminal?"
date: 2010-03-21
forum: General Help
---

### Post by TheNerdAL on 2010-03-21
So I have been having some issues with Ubuntu 9.10 and I think my computer isn't compatible, how can I be sure though? Thanks! :D

---

### Post by lisati on 2010-03-21
There are a number of tools available. One way is with the **dmideocde** command. Try:
```
sudo dmidecode
```

---

### Post by howefield on 2010-03-21
The one I like is

```
sudo lshw -html >hardware.html
```


This will place an html file in your home folder. Open with your web browser. A fairly well formatted record that will save you running the command again, (unless you change the hardware).

---

### Post by Brv on 2010-03-21
Better late than never, but I think "sudo lshw" is what you were searching for. It lists everything you need.

> sudo lshw~Brv

---

