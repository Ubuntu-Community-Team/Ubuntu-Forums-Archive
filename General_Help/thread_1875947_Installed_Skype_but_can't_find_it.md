---
title: "Installed Skype but can't find it"
date: 2011-11-05
forum: General Help
---

### Post by beastin on 2011-11-05
Hi, today I installed Skype in Kubuntu 11.10 using the Muon Software Center.  It now shows as installed at the software center, but I can't find it on my computer.  It is not in Applications->Internet in the K-menu, the search box doesn't find it, I can't run it from a terminal, and I can't find it with whereis from the terminal.  Any ideas?  Thank you, Bryan

---

### Post by oldos2er on 2011-11-05
By any chance are you using 64-bit Kubuntu? If so, it could be this bug: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all)

---

### Post by Script Warlock on 2011-11-05
reinstall using the site

---

### Post by dniMretsaM on 2011-11-05
This might work:
Alt+F2 -> skype

---

### Post by beastin on 2011-11-05
> **oldos2er said:**
> By any chance are you using 64-bit Kubuntu? If so, it could be this bug: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all)

 Thanks for the link!  That fixed my problem.  I am using the 64-bit version.  I uninstalled Skype in the Muon Software Center and then installed it from the terminal using the command
sudo apt-get install skype:i386 

 I don't really understand why that worked, but it did. 

Thanks again!
Bryan

---

### Post by oldos2er on 2011-11-06
Glad it worked! Would you please mark the thread as 'Solved' (under Thread Tools).

---

