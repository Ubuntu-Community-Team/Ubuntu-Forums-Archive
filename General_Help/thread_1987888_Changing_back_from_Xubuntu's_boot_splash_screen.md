---
title: "Changing back from Xubuntu's boot splash screen"
date: 2012-05-26
forum: General Help
---

### Post by forrestcupp on 2012-05-26
I originally installed plain Ubuntu 12.04. But I recently installed the xubuntu-desktop package just to have it as a choice. So after I did that, it also changed my boot splash screen to be the Xubuntu screen showing the loading bar before the login screen.

Does anyone know how I can change that back to Ubuntu's default? I didn't really want to switch the defaults to Xubuntu; I just wanted it as a choice.

---

### Post by ajgreeny on 2012-05-26
Try removing the plymouth packages that were installed along with xubuntu-desktop, possibly just **xubuntu-plymouth-theme**, but look for any others.

---

### Post by rai4shu2 on 2012-05-26
If you have galternatives installed, you can easily switch stuff like that (default.plymouth and text.plymouth).

---

### Post by forrestcupp on 2012-05-26
Thanks. It was **plymouth-theme-xubuntu-logo** and **plymouth-theme-xubuntu-text**. I tried from synaptic removing the main plymouth package, and that was going to remove about 500 packages that I knew I didn't want to remove. Those two did the trick, though.

Thanks for your help.

---

