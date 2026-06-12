---
title: "how to make ubuntu STOP spining down my Harddrives"
date: 2011-10-08
forum: General Help
---

### Post by kcirrab on 2011-10-08
i mainly use lubuntu but i assume the terminal command would be the same.. i want (lu)buntu to STOP sping down and shutting off my harddrives... i want to to run all the time because it takes to long to speed them back up.

need terminal command or simple instruction. Thank You!

---

### Post by Derek Karpinski on 2011-10-08
try installing packages:

sdparm or hdparm

note: neither of those were able to override the settings on my WD external drive, and I ended up writing a script that writes a hidden, empty file to the external drive every 5 min to keep the drive spinning.  I run the script as a cron job, and it only writes the file if the screensaver is NOT active.

If neither of the packages work, I'll give you my script.

---

### Post by Derek Karpinski on 2011-10-08
Before any of that........

Did you look at your 'Power Management' settings to see if 'Spin Down drives when possible' is checked on?

Is this a laptop?

---

### Post by kcirrab on 2011-10-08
no it is a desktop but it is old and i takes so long to get back to normal that its faster to restart the computer than to wait on them to spin up

---

### Post by kcirrab on 2011-10-08
synaptic says i already have hdparm installed. like i said i am in lubuntu because ubuntu is almost unuseable because this computer is sloooowww. like i said it says i have it installed but i dont know what to do from there

---

### Post by Derek Karpinski on 2011-10-08
assuming the drive you want to control is /dev/sda

```
sudo hdparm -S 0 /dev/sda
```

more on hdparm:

```
man hdparm
```

if that doesn't work, I'll post my script.

---

