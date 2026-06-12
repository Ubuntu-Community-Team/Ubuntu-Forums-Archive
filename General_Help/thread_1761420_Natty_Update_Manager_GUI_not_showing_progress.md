---
title: "Natty Update Manager GUI: not showing progress"
date: 2011-05-18
forum: General Help
---

### Post by marvin_littlewood on 2011-05-18
Hello!
 
When I run the update manager in XUbuntu (natty/11:04) it does not show its progress while installing the upgrades. 
 
After clicking on "install updates" and authenticating, there used to be a popup window with a progress bar and an option to show "details" but these appear to have disappeared in the last few days.
 
I don't recall switching these features off and there are no settings to restore them, available within the GUI. Is there another way of restoring this functionality?
 
If not, is a reinstall the way to go? If so what package(s) need re-installing? And in-case it is a configuration script, what files in my home directory need deleting to ensure a clean reinstall.
 
Thanks
 
Marv

---

### Post by el_koraco on 2011-05-18
try upgrading through the terminal before you go to extreme lenghts. 

```
sudo apt get update
sudo apt-get dist-upgrade
```

I doubt it has much to do with your config files, it's more likely a malfunctioning package.

---

### Post by marvin_littlewood on 2011-05-18
Thanks for your help. Did as you suggested...
 
The first command fetched all the package lists & read them without problem. The second upgraded "language-selector-common" and "language-selector-gnome" successfully. When the next upgrade notification comes down the pipe, I'll post the results of running the Update Manager GUI. FWIW Synaptic shows the same progress bar as the update manager should, when installing new packages.
 
If nothing changes, my inclination would be to use the command line to re-install upgrade-manager, synaptic and gdebi and see whether the problem is resolved.

---

### Post by marvin_littlewood on 2011-05-25
Tried re-installing upgrade-manager and upgrade-manager-core. Made no difference on my machine: there was no indication of progress. So now when upgrading a large number of packages, I have no idea how much there is left to do when using upgrade manager.
 
Thanks for your help everyone. Will report more as I discover it.
 
Marv

---

