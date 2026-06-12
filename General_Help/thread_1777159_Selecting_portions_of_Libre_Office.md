---
title: "Selecting portions of Libre Office"
date: 2011-06-07
forum: General Help
---

### Post by Scunnered on 2011-06-07
I have downloaded Libre Office 3.3.2 from the ppa and have found that in Applications > Office all the components of the programme are displayed.  My current interest only concerns calc and writer.

What is the best way for me only to have the two items available to me.  Can I install the redundant portions or should I just have them removed from the menu list?

Your guidance will be appreciated.

---

### Post by iclestu on 2011-06-07
> **Scunnered said:**
> I have downloaded Libre Office 3.3.2 from the ppa and have found that in Applications > Office all the components of the programme are displayed.  My current interest only concerns calc and writer.

What is the best way for me only to have the two items available to me.  Can I install the redundant portions or should I just have them removed from the menu list?

Your guidance will be appreciated.

suppose there is nothign to stop you doing
```

sudo apt-get remove libreoffice-impress
sudo apt-get remove libreoffice-draw

```
etc

---

### Post by Scunnered on 2011-06-07
**iclestu**

Many thanks for your assistance.  Followed your advice and it worked a treat.  I am unsure at times in matters like this and feel that is safer to ask.

---

### Post by iclestu on 2011-06-07
> **Scunnered said:**
> **iclestu**

Many thanks for your assistance.  Followed your advice and it worked a treat.  I am unsure at times in matters like this and feel that is safer to ask.

my pleasure entirely

---

