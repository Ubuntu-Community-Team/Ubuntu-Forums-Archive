---
title: "Printing from the CLI"
date: 2011-04-24
forum: General Help
---

### Post by Spiritof76 on 2011-04-24
I have a headless server running Lucid (10.4.2) connected to that printer is an HP 930C. I have cups running  and am able to initiate print jobs over the network from my desktop workstations. 

Wat I haven't figured out is how to print a textfile directly from the CLI Console.

I have an entry /dev/lp0 
My printers name is HP_DeskJet_930C

---

### Post by wt8008 on 2011-04-25
Take a look at lpr(1) [http://manpages.ubuntu.com/manpages/lucid/man1/lpr.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/lpr.1.html)

It will print to the default printer on the system by
```
lpr [ filename ]
```

---

