---
title: "cannot connect to localhost:631"
date: 2010-07-18
forum: General Help
---

### Post by kaykav on 2010-07-18
I cannot log into 'localhost:631' to install my printer. I reinstalled cups files to no avail.
            Why do you think I cannot login?...........thanks Rich

---

### Post by bobcollard on 2010-07-18
> **kaykav said:**
> I cannot log into 'localhost:631' to install my printer. I reinstalled cups files to no avail.
            Why do you think I cannot login?...........thanks Rich
Have you tried using the GUI Printing under System to install it?  I have two installed one hooked up USB and the other WIFI over a network.  Both were found and drivers installed using Printing.

---

### Post by kaykav on 2010-07-18
yes   ...   i can't make a connection to configure my printer.....

---

### Post by The Cog on 2010-07-19
First, see if anything is listening on that port:
```
netstat -lnt
```
If not, try 
```
sudo service cups start
```

---

