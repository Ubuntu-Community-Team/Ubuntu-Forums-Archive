---
title: "GRSync Error: Gtk-WARNING **: Error parsing gtk-icon-sizes string:"
date: 2010-06-17
forum: General Help
---

### Post by Rytron on 2010-06-17
Hi.
Here is an error that I got in Grsync:
```


(ssh-askpass:3955): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
sending incremental file list
	'panel-menu=24,24

panel=20,20
sent 280 bytes  received 12 bytes  53.09 bytes/sec
gtk-button=18,18
total size is 0  speedup is 0.00
gtk-large-toolbar=24,24'
```

How do I solve this? I am syncing my Ubunut PC to Linux Mint Laptop. I did not have any problems in previous weeks!

---

### Post by Rytron on 2010-06-18
I rank Grsync as my most important program. I tried again today. This is the error message.

---

### Post by Rytron on 2010-06-24
Eureka! I checked my exclude list and removed a few entries. Grsync still displays errors but now works. I use the 'Delete on destination' option and I think that some items on the exclude list were to be deleted but were not deletable (permission territory).

:p

---

