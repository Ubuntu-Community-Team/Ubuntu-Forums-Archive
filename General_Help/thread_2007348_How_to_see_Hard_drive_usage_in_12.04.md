---
title: "How to see Hard drive usage in 12.04"
date: 2012-06-20
forum: General Help
---

### Post by brevardo on 2012-06-20
How can I go into system settings to see how much space I have left on my 60 GB Hard drive. It seems to be impossible to find this in 12.04?

---

### Post by kanikilu on 2012-06-20
There should be a program called **Disk Usage Analyzer**. Type that into the dash.

I think it's included by default in 12.04, but it wasn't always there, so if for some reason it's not, just install it: ```
sudo apt-get install baobab
```

---

### Post by Cavsfan on 2012-06-20
Or just type into dash system monitor. It has a tab for File Systems which shows usage.

---

### Post by Cavsfan on 2012-06-20
Either one is good. I never knew about **Disk Usage Analyzer**. It came installed on my 12.04.
Thanks **kanikilu**

---

### Post by deadflowr on 2012-06-20
Just click on the home folder and enter the menu item view and click on status bar. The current status of your hard drive will be in the bottom panel of nautilus.

---

### Post by kanikilu on 2012-06-20
> **deadflowr said:**
> Just click on the home folder and enter the menu item view and click on status bar. The current status of your hard drive will be in the bottom panel of nautilus. Heh, don't get too attached to that method, it looks like they may be removing the status bar from Nautilus in 12.10 ;)

Of course, there is always **df -h** to get a nice summary of your disk free space if you don't care about knowing what is actually *using* the space - which is what baobab or du is for...

---

