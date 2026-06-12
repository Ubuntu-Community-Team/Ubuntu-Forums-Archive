---
title: "Update manger crashed, now I can't run it or synaptic or apt-get"
date: 2011-01-30
forum: General Help
---

### Post by spotrick on 2011-01-30
Help!

Update manager crashed last time I used it (although the updates seemed to happen OK.) Now it quits immediately if I try to run it, as does Synaptic. If I try apt-get from the command line, I get a Segmentation fault, e.g.

$ sudo apt-get autoclean
Reading package lists... Done
Segmentation faulty tree... 50%

How can I repair this? 

Running 10.10 on a Dell XPS M1330 laptop.

---

### Post by wilee-nilee on 2011-01-30
Try these commands.
sudo dpkg --configure -a
sudo apt-get -f install

---

### Post by garvinrick4 on 2011-01-30
Wilee-nilee has a typo:
sudo apt-get -f install

---

### Post by wilee-nilee on 2011-01-30
> **garvinrick4 said:**
> Wilee-nilee has a typo:
sudo apt-get -f install

Thanks for noticing, the cheat sheet got mixed up in editing.:)

---

### Post by spotrick on 2011-01-30
Thanks! That fixed it. :))

---

### Post by ashgoodman on 2011-03-25
Doesn't work for me. Still getting Segmentation faultsts... 0% on any update or upgrade attempts

---

