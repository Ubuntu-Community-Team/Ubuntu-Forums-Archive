---
title: "CUPS problems"
date: 2006-06-12
forum: General Help
---

### Post by brokenarrow on 2006-06-12
Hi,

Recently (8th of June) I did an apt-get dist-upgrade from Breezy to Dapper. This is my work computer and have currently access to a CUPS printer server. After the update I have had problems with the CUPS installation.  Currently I can see a lot of the work-printers and each time a user print on any of the 100 printers it pops up in the notification area ... pretty anoying!!

Ok, heres the deal.. It seems as if the cupsys does not start up properly, which seems odd... I get the error message when I try to do a

 > sudo /etc/init.d/cupsys restart

 * Starting Common Unix Printing System: cupsd 
    cupsd: Child exited on signal 15!

So in principle CUPS doesn't start up, however, I have no problems in printing..

Does anyone have some ideas what I should look for?

Thanks in advance,

---

