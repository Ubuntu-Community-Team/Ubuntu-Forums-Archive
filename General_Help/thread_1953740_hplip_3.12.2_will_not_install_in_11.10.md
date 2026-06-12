---
title: "hplip 3.12.2 will not install in 11.10"
date: 2012-04-06
forum: General Help
---

### Post by harlie on 2012-04-06
I downloaded hplip 3.12.2 from on line and have tried to install it numerous times. it looks like it is installing and yet when I try to print a photo from the upper tray with with my HP 6510 it will not print except from the lower tray with 8.5 x 11 inch paper. so when I check the installed version of hplip it still has only 3.11.7 and it will not properly operate my printer (an all in one) I can print anything from MS Windows but no way will Ubuntu print what I want. can someone tell me how to install hplip 3.12.2 on my desktop?

---

### Post by TeoBigusGeekus on 2012-04-08
Try purging the package
```
sudo apt-get purge hplip
```
and then reinstalling it.

---

### Post by harlie on 2012-04-10
> **TeoBigusGeekus said:**
> Try purging the package
```
sudo apt-get purge hplip
```and then reinstalling it.



ok I did this and now I have no hplip at all on my computer the driver will not install for 3.12.2. any other ideas? I  also downloaded again from both source forge and the hplip web site neither will install.

another strange thing is  in terminal when I type in dpkg -l| grep hplip then hit enter nothing happens it goes back to the prompt shown befor the command. Now I am altogether lost.:confused:

---

