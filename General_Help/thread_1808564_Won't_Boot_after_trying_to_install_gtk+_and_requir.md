---
title: "Won't Boot after trying to install gtk+ and required packages"
date: 2011-07-20
forum: General Help
---

### Post by mvarner00 on 2011-07-20
I was trying to configure my project using DigiESP (built on eclipse) and it told me that I did not have the gtk+ package installed to use gconfig so in the attempt to install gtk+ I somehow caused errors in my system when running the commands in terminal.  
 
Everything seemed to be going correctly with the ./configure, make, and make installs of the required packages but when i tried to install pango as instructed by [http://developer.gnome.org/gtk-faq/stable/c192.html](http://developer.gnome.org/gtk-faq/stable/c192.html) it said in the install file that i may need to run the command ldconfig, i believe, because it was seeing an old version installed and couldn't finish the ./configure command.
 
After running the ldconfig command in the terminal pango appeared to install correctly, however after doing so i was no longer able to start any new applications in gnome, I was still able to use the ones that were currently open but if i closed them they would not start back up.
 
In hopes that a reboot would solve the issue I pressed the power button to bring up the restart, shutdown, etc dialog since choosing restart or shutdown from the top menu produced nothing. 
 
Upon restarting the computer now hangs at the loading screen displaying Ubuntu 10.04 with four dots progressing across the bottom but never reaches the login screen.  If i press any key but enter it displays the cmd line and is showing that it is not getting past "checking battery state".
 
I have tried to remedy the issue by reinstalling the gnome-power-manager from the recovery option on bootup but have no luck.
 
I have also tried running the command in the command sudo dpkg-reconfigure xserver-xorg then startx in the recovery options as well as on the boot screen where Ubuntu 10.04 is displayed by using the Control-Alt-F1 but also no luck it spits out errors about invaild file format and shuts down the xserver
 
If anyone has any ideas on what I could try next that would be great!

---

