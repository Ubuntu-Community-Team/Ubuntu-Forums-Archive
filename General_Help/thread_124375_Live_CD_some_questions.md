---
title: "Live CD: some questions"
date: 2006-02-01
forum: General Help
---

### Post by tico on 2006-02-01
I'm trying Ubuntu on the Live CD to test it before I decide to install it. So, I have some questions to you:

1. How can I log in as root user using the Live CD?
2. I have a Canon Lide50 scanner, but xsane doesn't recognize it. I've read somewhere that a new experimental version of xsane can recognize it. Could you please tell me how to install (just to test) using the Live CD (I know it will be lost if I restart Ubuntu). I suppose I can do it, because I can install Firefox extensions and themes. But I need a very detailled How-to (where to dowload this new xsane version, every little thing to do).
3. Is there a way to automatically mount the NTFS partitions every time I boot (Ubuntu, on live CD, does it for the FAT partitions, but for the NTFS partitions, I need to mount them manually and it doesn't work very well: I cannot browse them using the Files Browser, only the disks tool)?

Many thanks in advance

---

### Post by adamonduty on 2006-02-01
1. Type sudo -s in the terminal. 
2. Open up the Synaptic package manager and search for xsane. Not sure which repository its in but it should you should be able to install it. If you don't find a newer version to update to, then the package probably hasn't been made for the new version.
3. Yes, you can find the instructions in the ubuntu starter guide (the help button on the panel) under Tips and Tricks.

---

### Post by tico on 2006-02-01
Hi, adamonduty,

Thanks for your answer. Concerning Synaptics, xsane's version used there is 0.97, but you can find a newer one (0.991). I've downloaded it, but I don't know how to install it. Could you please explain it to me?

---

### Post by tico on 2006-02-01
Concerning login as root, I would like to have a graphic session and this is only for terminal. Could you please tell me how to have a root graphic session (sorry for my ignorance, I'm a newbie in Linux)?

---

