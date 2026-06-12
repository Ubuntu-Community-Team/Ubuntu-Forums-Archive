---
title: "Cant Install"
date: 2011-01-13
forum: General Help
---

### Post by Mozesibe on 2011-01-13
Hay i need help immediately.
I cant install softwares again even from the Ubuntu software center. the error message says: Requires installation of Untrusted Packages.
what should i do?

---

### Post by Verbeck on 2011-01-13
you might need to refresh the software index
close any software center/ synaptic windows and from a terminal (applications>accessories) , enter *sudo apt-get update*
and post back if there are any errors. if not, try using the software center again

/do you have any non-official repositories added to the software souces?

---

### Post by Mozesibe on 2011-01-13
i've done dat- it did update but i cants till install apps from Ubuntu software center or anywhere else..plz do u have more advice?

---

### Post by Rubi1200 on 2011-01-13
Go to Applications > Accessories > Terminal

Run the following commands and post the output here please (especially if there are errors from the first 2 commands):

```
sudo apt-get install -f

sudo dpkg --configure -a

cat /etc/apt/sources.list
```

Thanks.

---

