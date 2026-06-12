---
title: "Where can I obtain Ubuntu Tweak"
date: 2010-12-09
forum: General Help
---

### Post by argedion on 2010-12-09
as the subject says I am looking on how to find Ubuntu Tweak? I have heard of this program but have no luck in finding it. I have searched in Synaptic and in Ubuntu software center the only thing I get is:
Ubuntu LTSP server management GUI
is this is or is it named Ubuntu Tweak?

---

### Post by wilee-nilee on 2010-12-09
I use the ppa.
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

### Post by karthick87 on 2010-12-09
Run the following in terminal,

Add the repository,
```
sudo add-apt-repository ppa:tualatrix/ppa
```Update your repository,
```
sudo apt-get update
```Install ubuntu-tweak
```
sudo apt-get install ubuntu-tweak
```

---

### Post by argedion on 2010-12-09
thanks.

is this a GUI or a command line thing? since i have never used it just curious of how I would use it.

---

### Post by argedion on 2010-12-09
I see its a GUI ok thanks guys

---

### Post by karthick87 on 2010-12-09
You have to type all those commands in your terminal(**Applications>>Accessories>>Terminal**)

After installation ubuntu-tweak will be found under **Applications>>System Tools>>Ubuntu Tweak**

---

