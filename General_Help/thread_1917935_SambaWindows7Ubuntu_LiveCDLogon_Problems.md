---
title: "Samba/Windows7/Ubuntu LiveCD/Logon Problems"
date: 2012-01-31
forum: General Help
---

### Post by ArticWizard on 2012-01-31
The situation:
Right now, I am typing from a laptop with a Windows 7 OS. I have a desktop with Win7 that has a failing hard drive. Right now that desktop is running on Ubuntu LiveCD and I have the HDD mounted and I can see that my files are still intact. I want to copy files from the desktop to the laptop through Samba.

The problem:
I cannot see my desktop on my laptop's Win7 Network, nor can I access the laptop from the desktop with Ubuntu Live(although I can see it). I'm prompted for a USERNAME, DOMAIN, and PASSWORD, but every variation I try does not work. The ethernet settings are fine. 

What is going wrong and how can I fix it?

---

### Post by Khayyam on 2012-02-04
ArticWizard ...

From a brief search I can see no reference to Samba being available on the LiveCD, I assume it isn't as its not generally something people would have any need of when installing. It could be installed (via apt-get) when booting the LiveCD but you would then need to configure it to reflect your user and shares.

One solution might be to use Turnkey's [Domain Controler Appliance](http://www.turnkeylinux.org/domain-controller) LiveCD. In terms of features its overkill, but as its primary goal is to serve as a Windows PDC, samba is already installed and running. Once booted user/shares can be quickly setup via its web interface.

HTH ...

---

