---
title: "[PPC] Daemons sending startup/shutdown console messages"
date: 2011-08-02
forum: General Help
---

### Post by Featalene on 2011-08-02
This is not one of the most critical issues but it is annoying. 

One daemon pbbuttonsd is writing to the console when I should have only the Ubuntu logo and the four dots during start up. I have several doing that during shutdown. Most of the ones during shutdown are mail related; sendmail, milter-greylist, clamav, and mimedefang, are the ones I recall. Though I believe there were one or two others. 

I'm not sure what route the messages elsewhere but I was guessing it is stop-start-daemon. Before I get too far into this I thought I would ask for any pointers on where to look more specific than the /etc/init.d files?

---

