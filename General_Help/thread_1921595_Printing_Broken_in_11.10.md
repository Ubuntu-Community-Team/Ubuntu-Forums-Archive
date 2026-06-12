---
title: "Printing Broken in 11.10"
date: 2012-02-07
forum: General Help
---

### Post by gr8 on 2012-02-07
My Canon MF4320d was printing fine in 10.10. I upgraded to 11.10 and printing is broken now. I get the error Idle - File "/usr/lib/cups/filter/pstoufr2cpca" not available: No such file or directory.

I've tried the suggestions in these forums to install a fake gs-esp package, uninstall and reinstall CUPS, and a few other things. None of them work. What a pain.

Anybody got this working in 11.10?

---

### Post by Linux Dutchman on 2012-02-07
Do this:
 
- open synaptic
- remove all canon drivers
- when all drivers are removed, close synaptic
 
Now go to this page: [https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers) and check the instructions at the bottom. 
 
This will add a repositorie to your software sources which contains a lot of Canon drivers. Try this to solve your problem.
 
I found something on this forum which contains a similar issue: [http://ubuntuforums.org/archive/index.php/t-1741672.html](http://ubuntuforums.org/archive/index.php/t-1741672.html)

---

