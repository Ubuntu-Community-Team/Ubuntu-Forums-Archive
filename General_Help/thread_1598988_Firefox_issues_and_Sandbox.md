---
title: "Firefox issues and Sandbox"
date: 2010-10-17
forum: General Help
---

### Post by ubutu on 2010-10-17
Hi, got two questions for ya,

1.For some reason, whenever I use F-fox (3.6.10 - canonical) to delete history, cache, etc via 'Clear recent history' option and select everything, some personal information still remains. For example, I just log-in simply by pressing 'u', then my username and password auto-fill. WTF.
How to completely erase ALL personal info from FF?

2. Javascripts. Scary stuff. Are there anything to run browsers in a virtual environment like Sanboxie to Windows? If your thinking chroot then I guess ya don't know Sandboxie. 

Just need to sandbox FF on the fly. I already have Vmware installed, so the list below seems pointless
OpenVZ:
Is like Vmware. Not it.

Linux Containers:
Like Vmware. Total system virtualization. 

[I]SELinux:
Whatever.............

etc, etc..........

[/I]

---

### Post by TeoBigusGeekus on 2010-10-17
1)Try with bleachbit. Otherwise, navigate to the ~/.mozilla/firefox folder and delete manually whatever you don't want.

---

### Post by ubutu on 2010-10-17
Thank you TeoBigusGeekus. It works.\\:D/

I didn't find a Linux equivalent Sandboxie, so here is the next question.....

What's the worst that can happen if one were to disable Noscript, FF extension and allow javascripts? 
   Sure, non-root accounts can't touch system files but bear in mind I consider my personal files more important than the system files which can easily re-install. 


thx

---

