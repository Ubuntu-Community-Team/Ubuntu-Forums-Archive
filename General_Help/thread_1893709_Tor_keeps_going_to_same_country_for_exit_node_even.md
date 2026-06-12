---
title: "Tor keeps going to same country for exit node even on firefox restart?"
date: 2011-12-10
forum: General Help
---

### Post by grflt on 2011-12-10
I have Tor configured not to save any cookies. I go to yahoo.com but it takes my to yahoo.XX where XX is a certain country code.  However, when I delete all my cookies, restart firefox, and go to yahoo.com again, it takes me to that same country code. Is my Tor installation compromised? How do I get it to use a different exit node when I restart firefox?

---

### Post by mutley89 on 2011-12-10
There is a setting that allows you to specify which exit nodes to use.  Have you set it inadvertently?  Check in your torrc file for something relating to ExitNode or see here:  
[https://www.torproject.org/docs/faq#ChooseEntryExit](https://www.torproject.org/docs/faq#ChooseEntryExit)

---

