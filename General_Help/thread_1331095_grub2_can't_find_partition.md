---
title: "grub2 can't find partition"
date: 2009-11-19
forum: General Help
---

### Post by Aliano on 2009-11-19
I've installed 9.10 and at the end of the install it looks for other os and finds my PCLinuxOS on sdb7.  When I reboot and select PCLinuxOS is gives message no such partition.  I tried command line to update grub and it finds pclos alright but the results are the same.  I've tried to find if anyone else has come across this and it looks like it's just me............Aliano

---

### Post by CookieNinja on 2009-12-09
It's probably no help to you, but I have a similar problem and trying to work out what is going on :-(

---

### Post by CookieNinja on 2009-12-09
One bios update later, and everything is working here :-D

---

### Post by oldfred on 2009-12-09
Lets see you entire boot configuration.

Boot Info Script 0.39 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 

Instructions
  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

cd to directory saved to: 
chmod 755 boot_info_script039.sh 
sudo ./boot_info_script039.sh 

or as example if on desktop from liveCD download 
sudo bash ~/Desktop/boot_info_script*.sh 

This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

