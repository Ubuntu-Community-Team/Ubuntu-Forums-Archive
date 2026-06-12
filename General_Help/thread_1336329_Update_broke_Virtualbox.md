---
title: "Update broke Virtualbox"
date: 2009-11-24
forum: General Help
---

### Post by Gary Nored on 2009-11-24
Todays update broke Virtualbox. What to do???

---

### Post by screaminfakah on 2009-11-24
You could try to reinstall it in Synaptic.  Make sure that you reload Synaptic first to update it incase there is a newer version of the program.

---

### Post by Gary Nored on 2009-11-24
Fixed. Had to download a new machine. Thanks for the reinstall suggestion -- it got me to thinking, so I checked with Sun, and sure enough, they had a newer one than mine. Installed, and it works perfectly. 

Gary

---

### Post by screaminfakah on 2009-11-24
No problem.  Glad to hear its fixed.

---

### Post by The Thug on 2009-11-24
The problem you have is that the VB driver is compiled on the current version of the installed kernel. So for any kernel update that you download (such as today's), you have to re-compile the VB driver.

When you start VB after a kernel update, you will generally get an error message that says something to the effect of running the following command as root "/etc/init.d/vboxdrv update". This command will re-compile the driver using the latest kernel. 

You don't have to download and re-install VB.

Hope that helps.

---

