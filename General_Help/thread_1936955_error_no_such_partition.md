---
title: "error no such partition"
date: 2012-03-06
forum: General Help
---

### Post by nadtribble on 2012-03-06
Hi everyone.  First of all I tried to install Unbuntu 11.1 on my desktop computer.  Turned out to be the sever instead.  So I erased the partition ( probably wrong thing to do. ) and now my window xp wont reboot.  I get no such partition error and grub rescue>
any help please.  I'll try to install the desktop version if I can get this fixed. but it won't boot to windows
thanx
nad

---

### Post by raja.genupula on 2012-03-07
Reinstall Grub is the best solution 
[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jerrrys on 2012-03-07
Hi Raja

@OP
Reinstalling grub may be the best answer, but a simple way would be just to reinstall the server edition.  This will restore grub and windows.  Then for adding the ubuntu-desktop do this:

Press Ctrl Alt F5

And enter the required information.  You will not see any confirmation when entering your password.  Then enter the following commands one at a time:

sudo apt-get install ubuntu-desktop

sudo reboot

That will give you a complete ubuntu install without burning another cd.

any questions?  post back

---

### Post by nadtribble on 2012-03-07
thankyou, will try Jerrrys suggestion later tonight

---

### Post by nadtribble on 2012-03-07
Thankyou very much Jerrry. Got the desktop working.  Now I was wondering if I can disable the grub.  And go back to windows xp as my default 1st boot and have the boot menu read
Windows xp
Windows xp recovery
ubuntu
thanx
nad

---

### Post by jerrrys on 2012-03-07
yes you can

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=default+to+windows+xp&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=default+to+windows+xp&sa=Search&cof=FORID:9)

---

