---
title: "how to add printer in Lucid"
date: 2010-08-15
forum: General Help
---

### Post by joepotter on 2010-08-15
I have a fresh install of 64bit Ubuntu Lucid and I can not install a printer in the manner that I have been doing for some years now. I would like to click on System --> Administration --> Printing and then Add but it is grayed out and the applet has not connected to the Cups Server. This is the long term service edition and it would seem that printing is broken: at least at this location. 

Does anyone have any ideas or suggestions as to this matter?

---

### Post by cogier on 2010-08-15
Can you get to [http://localhost:631/]("http://localhost:631/")?

If you can't then you can try and restart CUPS with
```
sudo /etc/init.d/cups restart
```

Then see if the printer dialogue is still greyed out.

Hope that helps.

---

### Post by joepotter on 2010-08-15
I was forced to restart cups, but that did work. The question becomes why cups did not start automatically and if this is a widespread problem or just an anomaly with my 64 bit install. Unfortunately I do not have time to check out the bug reports and see if this has been reported. I'll do that later if I get the free time.

---

