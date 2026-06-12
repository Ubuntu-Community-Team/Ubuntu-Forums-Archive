---
title: "Upgrade manager won't update... held packages..."
date: 2011-05-29
forum: General Help
---

### Post by lspear76 on 2011-05-29
I haven't been able to run upgrade manager in a few days. it started when something called evince wouldn't upgrade (it would be on the list, but when i would try to upgrade it, it wouldn't finish). now nothing shows up in the upgrade manager. 

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

I don't understand what this means or how to fix it.

I installed Gnome 3 desktop (via ppa) a few weeks ago along with LDXE because I don't like Unity.

---

### Post by linuxinstalledfromhdd on 2011-05-29
You would have been better off using a "stable" environment like Gnome 2. And you can easily use Gnome 2 (Classic Ubuntu) by doing this right after you install Ubuntu:

Click on top left corner of Unity. Type in the search box for Login.  Unlock. And select from the dropdown menu Ubuntu Classic. And exit to  save. Reboot to make sure the changes have taken effect.

You can "try" to fix your system by performing a PPA Purge of your Gnome 3 repository, or you can simply wipe the entire system and start fresh.  Other than that you are SOL

---

### Post by Frogs Hair on 2011-05-29
If you have done a distribution upgrade to Gnome 3 you will have to fix Gnome 3 or reinstall . Evince is the pdf reader for gnome . You no longer have a gnome 2 option on your system .

I don't use Gnome 3 , but open the terminal and try these commands. 
```
sudo dpkg reconfigure -a
``````
sudo apt-get update
``````
sudo apt-get upgrade
```

---

