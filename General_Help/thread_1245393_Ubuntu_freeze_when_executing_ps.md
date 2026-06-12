---
title: "Ubuntu freeze when executing ps"
date: 2009-08-20
forum: General Help
---

### Post by fowie on 2009-08-20
Ubuntu 9.04 base install with xbmc and ssh installed.  Screen freezes but I can still ssh into the machine.  I can run basic commands (ls, scp, top) but if I run 
```

ps a

```
or
```

ps aux

```
it will start printing the process list and then hang.  I can open a new window and SSH in again, but I never get control back at the original ssh terminal.  Note that 
```

ps

```
works fine, but even
```

ps u

```
will freeze the terminal.  How else could I get a printout of the process that's causing the hang, and how can I kill it, since even trying to kill certain processes hangs the terminal??

---

### Post by rayit on 2009-09-09
I have same problem, someone idea??

gr
Raymond

---

### Post by fowie on 2009-09-09
The only thing I've been able to figure out so far is that it was my XBMC.bin process that was causing the freeze.  Any attempt to do anything with that ps (pidof, kill, etc...) would cause my terminal to freeze. No help on the XBMC forums though. Any one here able to shed more light?

---

### Post by ynaes on 2009-09-10
Having the same issue here on Ubuntu Server 8.04.  Not running anything other than some Xen domUs and Samba.  All seemed to be working fine until I rebooted yesterday - Perhaps some recent updates caused this?

---

