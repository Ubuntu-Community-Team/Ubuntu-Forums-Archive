---
title: "Missing Windows Control buttons?"
date: 2010-05-02
forum: General Help
---

### Post by Algus on 2010-05-02
After upgrading from 9.10 to 10.04 I lost my windows control buttons (minimize, maximize, close)

Browsed the forums and found the suggestion of: 

```
metacity --replace
```

Command works to restore my buttons but I've got a couple problems

1. I have to leave this terminal open permanently.  If I try to close it (and "kill" the process) not only do I lose my windows controls but my keyboard stops working entirely.  

2. Have to put this in every time I log back in.

Is there a better solution for restoring my windows control buttons (ie one that doesn't require me to open a terminal every time I log in?)

---

### Post by dv3500ea on 2010-05-02
Go to System -> Preferences -> Startup Applications
click Add
type:
```
metacity --replace
```
into the command text box
click Add

---

### Post by Algus on 2010-05-02
That didn't seem to do anything.  Well, it did make the screen flash once upon initial loading.  I still had to punch the command into the terminal to get my borders back though.

---

### Post by BigSilly on 2010-05-13
Hmm. I'm getting this problem sporadically too. Happens just as the OP describes it.

Is there a fix? Should I file a bug report, or has one already been set for this issue?

---

### Post by daneskildsen on 2010-06-13
Hi there

I have exactly the same problem. Does anyone know how to resolve this??

Regards,
Dan

---

### Post by wilee-nilee on 2010-06-13
Here is one bug report.
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/408764](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/408764)
Basicaly I think it is related to graphic card drivers. In the terminal
```
lspci | grep VGA
``` 

This will tell you the card and you can look in synaptic and see whats running it, the generic is generally preferred in some cases. You can also Google for info on your own particular card, and post what it is for others to help. Really though each should start a independent thread.

---

### Post by daneskildsen on 2010-06-14
When I do "lspci | grep VGA" I find out that my VGA compatible controller is "Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)" but I don't know how to use that information in Synaptic.

---

### Post by thatbreegirl on 2010-06-15
Go to System -> Preferences -> Startup Applications

disable devilspie, reboot

I removed it completely and buttons returned after reboot.

---

### Post by BigSilly on 2010-07-10
> **thatbreegirl said:**
> Go to System -> Preferences -> Startup Applications

disable devilspie, reboot

I removed it completely and buttons returned after reboot.

Hmm. Well I don't even have that program installed, yet I still get this problem when I boot up. At the moment if I use the Compiz Fusion icon and reload the window manager, the buttons appear. But it's not a long term solution and the problem will often reappear at the next boot. It doesn't happen every time though, which is probably why you thought it had gone on your next boot.

Any other ideas? It seems to be a Compiz issue.

---

### Post by vicohm on 2010-07-25
You want to make metacity permanent? You can do that by removing compiz using the command
> sudo  apt-get  remove  compiz
sudo  apt-get  remove  compiz-core
Worked for me..

---

### Post by nalgarryn on 2012-04-11
> **daneskildsen said:**
> When I do "lspci | grep VGA" I find out that my VGA compatible controller is "Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)" but I don't know how to use that information in Synaptic.

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)

I'm having this same problem. I only started using this window manager after updating to 11.10 though. My window controls disappeared after maximizing and then minimizing Opera. There is only a couple pixel width between the menubar at the top of the screen and the top of the Opera window - I have the tabs shown and nothing above that. My terminal works properly (the puple background one) but again has no window border or controls. I'm guessing it might be related to my video controller if it's uniform with hardware.

---

### Post by oldos2er on 2012-04-11
Closed. nalgarryn, please start a new thread, since this one is two years old.

---

