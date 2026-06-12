---
title: "Ubuntu will not load GUI -- screen flashes at Ubuntu splash screen"
date: 2010-05-21
forum: General Help
---

### Post by xluke on 2010-05-21
Hello,
Out of nowhere Ubuntu (intrepid, I believe) has stopped loading for me.  When it attempts to load gdm the screen starts flashing at the splash screen and then eventually dumps me to the terminal.  From there I can login without any problems but can not get the GUI to load.  

When I run sudo gdm-binary it does the flashing splash screen again and then spits out the error message: WARNING: Unable to find users: no seat-id found.  Then a few warnings about longest graphic displayed 2.5xxx seconds
I tried running sudo dpkg-recondifigure gdm and relaunch gdm as above and it did the same thing.

I was not able to successfully connect to my wireless network through the terminal to try to update in the hopes of that fixing the problem.  Perhaps someone can give me instructions on how? (I have tried but can not figure out how to initialize wlan0).  

Or, is there something I can do from my installation CD?  

Thanks!

---

### Post by dcstar on 2010-05-21
> **xluke said:**
> Hello,
Out of nowhere Ubuntu (intrepid, I believe) has stopped loading for me.  When it attempts to load gdm the screen starts flashing at the splash screen and then eventually dumps me to the terminal.  From there I can login without any problems but can not get the GUI to load.  

When I run sudo gdm-binary it does the flashing splash screen again and then spits out the error message: WARNING: Unable to find users: no seat-id found.  Then a few warnings about longest graphic displayed 2.5xxx seconds
I tried running sudo dpkg-recondifigure gdm and relaunch gdm as above and it did the same thing.

I was not able to successfully connect to my wireless network through the terminal to try to update in the hopes of that fixing the problem.  Perhaps someone can give me instructions on how? (I have tried but can not figure out how to initialize wlan0).  

Or, is there something I can do from my installation CD?  

Thanks!

You may have to edit/replace the /etc/X11/xorg.conf file to basic default settings.

You should be able to search out detailed instructions in existing threads.

---

### Post by xluke on 2010-05-21
Bingo!  Thanks a lot! 

At the terminal I just did "sudo rm /etc/X11/xorg.conf" and rebooted.  All seems well.  

Thanks again.

---

