---
title: "Printing Problems on natty via parallel port"
date: 2011-07-30
forum: General Help
---

### Post by fidis on 2011-07-30
After installing natty on my new pc (with Asus mainboard and an additional pci card supplying a parallel port)
i can not print anymore over cups.

When i copy a file directly to /dev/lp1 as root it is being printed. 
When i do the same with my userid it is not being printed.

When i print the testpage in the printing app or from any other application, the print  job stays in status "processing - not connected" and nothing happens.

I have attached the requested debugging information.

It would be really great if somebody could help me.

thanks very much in advance 

Friedemann

---

### Post by fidis on 2011-08-01
I really would aperciate some help

---

### Post by fidis on 2011-08-05
printer is still not working help would be great.
otherwise i entered all the debugging information for nothing

---

### Post by fidis on 2011-08-06
now i managed to find the solution.
 it is printing !
i added my user to the group lp in /etc/group

---

