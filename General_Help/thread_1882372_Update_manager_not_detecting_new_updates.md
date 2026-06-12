---
title: "Update manager not detecting new updates"
date: 2011-11-17
forum: General Help
---

### Post by Rob0147 on 2011-11-17
hi guys

I have 2 machines both with ubuntu 11.10 on them. On one of my machines, it doesn't seem to be detecting new updates in update manager and has not downloaded any new updates in the last 20 days. My other machine however has been detecting and downloading them OK so I know there are some new updates to install.

Please can someone help me to ascertain what the problem is on the problem machine.

many thanks

Rob

---

### Post by DogMatix on 2011-11-17
If you run:

```
sudo apt-get update
```

in a terminal window, do you see errors at the end of the output?

---

### Post by philinux on 2011-11-17
Open a terminal.

sudo apt-get update

Then

sudo apt-get upgrade

Post back any errors.

---

### Post by Rob0147 on 2011-11-17
Hi Guys

I ran the two commands as advised and my machine downloaded a whole bunch of updates with no errors so I think the problem is now resolved.

thanks very much for your help

regards

Rob  :p

---

