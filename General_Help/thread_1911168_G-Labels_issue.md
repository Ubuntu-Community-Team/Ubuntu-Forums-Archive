---
title: "G-Labels issue"
date: 2012-01-18
forum: General Help
---

### Post by Scott Baker on 2012-01-18
Howdy all, hopefully someone can assist with this issue. I am using G-Labels on my desktop, which runs Ubuntu 11.04, and Edubuntu 11.04. The problem I'm running into is when I set my labels up using a pre-designed template ( example, Avery 8660 ), it sets up fine. But when I go to print my labels ( H/P deskjet D-4360 ) the formatting is off, and the labels print "low", causing me to lose the bottom third of my label ( the labels print fine, with no loss of text or graphics ). It's just that they print outside of the label boundries. Is there a way that I can access the pre-designed templates files and correct them, so that I can move my text and graphics back "up" onto the labels for final printing ??  ](*,)

---

### Post by wolfen69 on 2012-01-18
Have you done an alignment for your printer?

---

### Post by Scott Baker on 2012-01-18
First thanks for the fast response. My printer has been aligned, and double checked. Alignment doesn't seem to be an issue, but I'm not entirely sure. If you could provide a little more info as to how to perform a thorough check on my printer, that would be appreciated. I have suspected that this printer may have an issue within the Ubuntu operating environment, because I hadn't had any issues when it was sharing with my wifes Vista install ( it worked fine with Vista ) Thanks again.

---

### Post by wolfen69 on 2012-01-18
What kind of printer is it? Do other things print OK?

---

### Post by Scott Baker on 2012-01-24
Sorry for the delayed response. The printer in question is a Hewlett-Packard D4360 inkjet. As far as I can tell, there doesn't seem to be any other issues, but normally I'm printing basic text based documents. I see that Ubuntu has quite a bit of H/P listed in synaptic. Do you happen to know if they have a testing and set up package similar to the package that's offered for Windows? (H/P has a Windows diagnostic and set up program that allowed very precise alignment with my wifes former Vista install). Thanks much for the help.

---

### Post by wolfen69 on 2012-01-24
HP has a utility called HPLIP Tools.
```
sudo apt-get install hplip-gui
```

---

### Post by Scott Baker on 2012-02-01
First, sorry for the late response. Reinstalled the previous mentioned package ( it had  been installed before I upgraded to 11.04 ) That seemed to take care of the issue. Thanks much, appreciate your time. :D

When you want to try something, you use Windows. When you want to ***DO*** something, you use Linux.  \\:D/

---

