---
title: "Deja Dup Full System restore PROBLEMS"
date: 2011-03-16
forum: General Help
---

### Post by OttoMann on 2011-03-16
Hi!

I have an major problem restoring my entire system back to working order.

I have and dual boot system WinXp+Ubuntu 10.10. 
Ubuntu is installed on 3 partitions (/, /home, and SWAP), WinXp has it's own partition.

Using Deja Dup I made a complete system backup (/,/home) to an external usb disc.
After fooling around with another Linux distro (instaling it over the Ubuntu) I decided to restore backed up Ubuntu 10.10.

How do I do this?

I tried to install Ubuntu and then run restore from Deja Dup, but system chrashes when the restore comes near the end. I tried to run Deja Dup from live session, but it don't seem to find the linux partitions.

What to do?

P.S.
As you can see from the post I am pretty noob-ish....

---

### Post by OttoMann on 2011-03-18
O.K. solved this one with the help on some other forum.

The trick is to reinstall and then use Duplicty in the command line to extract the contents of /home from the backup.

---

