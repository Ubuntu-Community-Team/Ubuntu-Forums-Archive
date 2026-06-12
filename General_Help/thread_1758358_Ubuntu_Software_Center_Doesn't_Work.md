---
title: "Ubuntu Software Center Doesn't Work?"
date: 2011-05-14
forum: General Help
---

### Post by funkystudios on 2011-05-14
Hi. I just installed Ubuntu and have opened software center a couple times. Installed Google Chrome, and played around with Ubuntu a little bit. Now when I try to open software center, it just is a window with grey. (Attached image). Any advice? To get it back, I have to restart Ubuntu...

---

### Post by funkystudios on 2011-05-14
Ok, well. I partially figured it out... (I think) I noticed that USC is running in the background all the time, before I try to open it. I killed that process, and I opened it up. It works now. I'm hoping that this won't keep happening!

---

### Post by gabak on 2011-06-26
this help me kind to fix the problem

[http://ubuntuforums.org/showthread.php?t=1791038&highlight=software+center](http://ubuntuforums.org/showthread.php?t=1791038&highlight=software+center)


try this series:

Clean up your package installation

If you have installed and uninstalled a lot of applications, chances are your system is infected with a lot of dependencies files that you have absolutely no use for. Here are some useful commands to get rid of any partial package and remove any unused dependencies:
Cleaning up of partial package:
sudo apt-get autoclean

Cleaning up of the apt cache:
sudo apt-get clean

Cleaning up of any unused dependencies:
sudo apt-get autoremove

A good practice to avoid any left behind is to use the autoremove command whenever you want to uninstall an application.
sudo apt-get autoremove application-name

---

