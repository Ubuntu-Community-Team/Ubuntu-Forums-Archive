---
title: "Cups Problem(s)"
date: 2010-02-17
forum: General Help
---

### Post by amurph1111 on 2010-02-17
Hi. I am new to the forum, but have somewhat of a moderate experience with ubuntu based operating systems. I am running Karmic right now, but I have had this problem with cups ever since the fresh install a month or so ago. The disc I used for the install was a little scratched up, and files may have been corrupted, but after the install everything ran fine. Except for cups

Cups will not connect and the service will not run. Neither at boot, or if I try to start it manually. When I type in terminal: cupsd ' it will say: cupsd: Child exited on signal 15!

The only way I can get it to run is to reinstall the cups package. Then printing will work beautifully, of course, until I reboot. I have tried downloading a whole new cups package from the internet, and completely removing the cups that I had installed, including config files. Then I install the fresh cups, and it does the exact same thing. So, in other words, Is it cups that is the problem, or something else?

If i go into system-config-printer and click connect, is fails. If i go to localhost:631, page cannot be displayed.

Does anybody have any ideas whatsoever? It would be great If i didn't have to reinstall cups every time I wanted to print a service bulletin.

Thank you very much to anybody who is willing to help me out.

---

### Post by amurph1111 on 2010-02-17
bump?

---

### Post by amurph1111 on 2010-02-17
nobody huh. I found a thread like mine, but it was caused by the cupsd.conf file being empty. Mine is not.

---

