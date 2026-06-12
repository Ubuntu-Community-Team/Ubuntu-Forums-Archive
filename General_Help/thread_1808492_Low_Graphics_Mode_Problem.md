---
title: "Low Graphics Mode Problem"
date: 2011-07-20
forum: General Help
---

### Post by hello cruel world on 2011-07-20
After resolving a lot of errors with my ubuntu triple boot machine, I have been woefully greeted by low graphics mode. My system was working fine. I restarted the sytem after a package update and was greeted with the error. 

When I try to run in low graphics mode it opens to just background with no keys or gui working. 
When I go to reconfigure your display, no matter which button I select it just resets the menu.
When I go to troubleshoot error, it will let me view xserver log and startup errors but it wont let me edit configuration.
When I go to command mode trying to run sudo apt-get update it wont update.  I was also told it is download -only mode.
When I click restartx it gets stuck at load screen.

In recovery mode:
dpkg did not work
netroot experienced same inability to update
failsafex failed and returned to recovery menu

I tried to follow this, but can't get it to update:

 sudo apt-get update 
sudo apt-get -d install --reinstall gdm 
sudo apt-get remove --purge gdm 
sudo apt-get install gdm sudo apt-get remove --purge xserver-xgl compiz compiz-plugins compiz-core compiz-manager csm cgwd cgwd-themes 
sudo apt-get install --reinstall compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins libcompizconfig0 
sudo dpkg-reconfigure -phigh xserver-xorg

---

