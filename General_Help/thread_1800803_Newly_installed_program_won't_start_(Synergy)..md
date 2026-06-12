---
title: "Newly installed program won't start (Synergy)."
date: 2011-07-09
forum: General Help
---

### Post by LtdEdFred on 2011-07-09
Hello.

I wanted to try [Synergy](http://synergy-foss.org/) but some problem [(official bug in 11.04)](http://synergy-foss.org/pm/issues/2946) makes it impossible to install it through the package manager so I downloaded the .deb file and installed it in the terminal using dpkg -i. The Synergy icon pops up in my menu but when I click it nothing happens. Is there anything I can do to force it to start?

---

### Post by fragos on 2011-07-09
Try initiating Synergy from the command line in a terminal window. There may be messages displayed helping you identify the issue.

---

### Post by Randy Flagg on 2011-07-09
Did you set up the cfg file on the server and client? I am running synergy on 11.04 ubuntu and a win 7 machine and it works fine.  I did find that there isn't a log of error notifications.  It either works or it doesn't.

I also found that the the gui configuration didn't work well but editing the cfg files is pretty easy.

---

### Post by LtdEdFred on 2011-07-17
I appreciate your help and apologize for my late reply but I've been on vacation.

> **fragos said:**
> Try initiating Synergy from the command line in a terminal window. There may be messages displayed helping you identify the issue.
I tried this without luck.

> **Randy Flagg said:**
> Did you set up the cfg file on the server  and client? I am running synergy on 11.04 ubuntu and a win 7 machine and  it works fine.  I did find that there isn't a log of error  notifications.  It either works or it doesn't.

I also found that the the gui configuration didn't work well but editing the cfg files is pretty easy.
I followed a guide I found and edited the conf file according to that but I still couldn't get a connection between the computers. :confused:

---

### Post by nbolton on 2012-07-30
If installing Synergy 1.4 on Ubuntu 11.04 and below, you need to run the following command before it will start.

```
sudo apt-get install libqt4-gui libqt4-network
```

---

### Post by wildmanne39 on 2012-07-30
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

