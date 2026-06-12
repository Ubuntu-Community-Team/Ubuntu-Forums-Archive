---
title: "Update error"
date: 2006-06-02
forum: General Help
---

### Post by kyoushu on 2006-06-02
Well, I had ubuntu 5.10, and had recently upgraded to the 6.06 beta(about a week and a half ago.  Well, I got an update notification but when I click the little orange star thing the Software Updates window opens but then another window also pops up saying > 
Please close the other application e.g. 'aptitude' or 'Synaptic' first.

Dunno why.  Then, if I right click on the orange thing and click Install all updates, a window opens saying Error >  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


Well, if anyone could help, that'd be great.

---

### Post by johnc4510 on 2006-06-02
First problem, you can only have one package manager running at a time, if more than one is running, up can not install or update anything.Package managers are:
      Synaptic Package Manager
      In a terminal:apt-get or aptitude
      Update Manager
If you have more than one running close until only one is running.

Second problem, open a terminal:
Applications>Accessories>Terminal
Copy and Paste the following to it:
sudo dpkg --configure -a
This should correct the problem

---

### Post by kyoushu on 2006-06-02
For the first one, I don't know of any other package managers I have running(I've restarted and still same errors).  Im trying out sudo dpkg --configure -a now, if that doesn't work Ill post again.

---

### Post by kyoushu on 2006-06-02
Well, after doing sudo dpkg --configure -a, it opened and installed the updates.  Thanks a bunch johnc4510

---

