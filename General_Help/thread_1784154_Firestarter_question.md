---
title: "Firestarter question"
date: 2011-06-16
forum: General Help
---

### Post by masonstorm on 2011-06-16
Hello,

Can someone tell me what the purpose of checking the "block traffic from reserved addresses on public interfaces" under advanced options is supposed to do in Firestarter?  If I check this option and my firewall keeps getting hit from various locations some being 184.51.207.32 and .26, .59, etc.  When I look these up it seems they are coming from akamatitechnologies.  If I uncheck this option no hits.  What are the best settings for Firestarter?  I'm a total noob to Linux so please forgive me if I ask a lot of questions.  Thanks!

---

### Post by wildmanne39 on 2011-06-16
> **masonstorm said:**
> Hello,

Can someone tell me what the purpose of checking the "block traffic from reserved addresses on public interfaces" under advanced options is supposed to do in Firestarter?  If I check this option and my firewall keeps getting hit from various locations some being 184.51.207.32 and .26, .59, etc.  When I look these up it seems they are coming from akamatitechnologies.  If I uncheck this option no hits.  What are the best settings for Firestarter?  I'm a total noob to Linux so please forgive me if I ask a lot of questions.  Thanks!
Hi, firestarter is very old it should not be used anymore. I was told to use this instead. gufw Install it by typing this in a terminal
```
sudo apt-get install gufw
```

---

### Post by masonstorm on 2011-06-17
Thanks.  I'll give that a try

---

### Post by wildmanne39 on 2011-06-17
> **masonstorm said:**
> Thanks.  I'll give that a tryHi, your welcome if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by masonstorm on 2011-06-22
> **wildmanne39 said:**
> Hi, your welcome if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.
I uninstalled Firestarter and installed GUFW.  How do I know its working properly?  I launched it and checked the enabled option and made sure that it was denying incoming traffic and allowing outgoing traffic.  Under preferences I unchecked enable GUFW logging and kept enable ufw logging checked.  Is that all there is to it?  I just want to make sure when I have to take my laptop to a WIFI hotspot the firewall is working properly.  Thanks!

---

