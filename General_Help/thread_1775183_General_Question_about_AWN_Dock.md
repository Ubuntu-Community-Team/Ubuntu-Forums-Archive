---
title: "General Question about AWN Dock"
date: 2011-06-04
forum: General Help
---

### Post by neu5eeCh on 2011-06-04
Preliminary: So I was noodling around with AWN and I was installing *something* (related to AWN). I was warned that if I proceeded installing the package, then XFCE Desktop (etc.) would be uninstalled. I said to myself: No way; but cool, I'll try that in Virtual Box. It looked as though AWN was going to replace my desktop with its own DE (panel, etc.). Problem is, I can't get back to that option.

 Does anybody know what I did and need to do?

---

### Post by ankspo71 on 2011-06-04
Hi,
What was the name of the package? Is the Virtualbox installation of Xubuntu the same version as your installed version of Xubuntu? What you are describing sounds more like a dependency problem more than anything else. It is generally not a good idea to install something if it requires the removal of something else, unless you are sure you no longer need those packages. 

For example, if the AWN related package required package 'abcdef' version 3.2, but XFCE was only compatible with package 'abcdef' up to version 3.0, then that would be a reason for it to want to uninstall XFCE.

Step 1
If you already installed the AWN related package causing it to remove XFCE, then I recommend uninstalling that AWN related package, then reinstall xubuntu-desktop (unless you don't mind not having the missing packages). If you used Synaptic Package Manager to install the AWN related package, you can use the built in history feature (File Menu > History) to see which packages were installed at the time and then remove them one by one, or you can open your terminal and use the following commands.

```
sudo apt-get remove AWNrelatedpackage
sudo apt-get autoremove
sudo apt-get install xubuntu-desktop
```

Step 2
Sometimes when we install packages, those packages will automatically install "recommended" packages too, and maybe it was one of those recommended packages that caused the removal of XFCE. If this is the case, then installing the AWN related package with the "--no-install-recommends" option might help. It's a slim chance that this will help though. 

```
sudo apt-get install AWNrelatedpackage --no-install-recommends
```

If that doesn't help, then it is safe to say that the AWN related package is not compatible with the XFCE desktop yet (or xubuntu-desktop).

Hope this helps.

---

