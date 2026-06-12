---
title: "no keyboard at log in??!"
date: 2011-05-06
forum: General Help
---

### Post by FLCL on 2011-05-06
This just started happening last night and it's annoying as hell. I log in fine, and bam, no keyboard. I have to go to System>preferences>input method switched, switch it to sysadmin default>lock screen>switch user>log back in> THEN IT WORKS.

How can I have my keyboard back? I read on a similar old thread to copy .config and copy it to a different user then delete it from home directory. Will all of my preferences go away if I delete it?

---

### Post by dino99 on 2011-05-06
you should check /etc/default/keyboard 

or reconfigure it: sudo dpkg-reconfigure keyboard-configuration

or manually: system pref keyboard

and clean the system too
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -phigh -a  (could take a while, dont stop it)

---

