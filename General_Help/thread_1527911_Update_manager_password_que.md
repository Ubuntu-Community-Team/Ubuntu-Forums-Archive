---
title: "Update manager password que"
date: 2010-07-09
forum: General Help
---

### Post by NotHandy on 2010-07-09
I've got Ubuntu Hardy Heron 8.04, I've used it for years, I'm not a tech. savy person but I've managed to do everything I want to it, and with it. I've just run into a problem that I can't find a solution to. Right now I have some updates ready to install but when I click on the install updates button, I get the twirling wait signal and it goes on forever. I've left it alone to wait for it as long as 15 min. waiting to give it my pass word to go ahead and install but it never gets to the pass word input box. One thing I tried was to restart the computer at an earlier updated time (only tried it once) but it didn't change. If anyone knows of a solution please make it a detailed step-by-step, as I'm not a programmer but I can figure a few things out. Thank you!

NotHandy

---

### Post by NotHandy on 2010-07-10
What? no answers? I've still got 4 updates to install and my update manager won't initiate the password sign-on.....what to do....Thought I'd post this reply to send it to the top again, right now I'm on page 16 or so and I posted it yesterday. Lots of traffic on here. My post has been looked at 22 times with no reply

---

### Post by hawthornso23 on 2010-07-10
Have you tried doing this through Synaptic? Start up synaptic 

System - Administration - Synaptic Package Manager

Click "mark all upgrades" and then click "apply". 

There is also a way of updating via the command line. Someone will no doubt remind us of that in a minute. But try the synaptic thing first.

---

### Post by theozzlives on 2010-07-10
> **hawthornso23 said:**
> Have you tried doing this through Synaptic? Start up synaptic 

System - Administration - Synaptic Package Manager

Click "mark all upgrades" and then click "apply". 

There is also a way of updating via the command line. Someone will no doubt remind us of that in a minute. But try the synaptic thing first.

It's:
```
sudo apt-get upgrade
```
BTW: there's a new LTS, it's called 10.04 Lucid Lynx.

---

### Post by NotHandy on 2010-07-10
The synaptic package manager didn't work because it couldn't load the admin, log-in screen. But the terminal did work with typing in my password and the update is almost complete, I just need to restart the computer and I'll try the update manager again afterwards. (when I get another update to install) Thank you very much for your help!!

NotHandy

---

