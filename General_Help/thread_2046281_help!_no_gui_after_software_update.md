---
title: "help! no gui after software update"
date: 2012-08-22
forum: General Help
---

### Post by apexone4697 on 2012-08-22
I need help.  I have win 7 and Ubuntu 12 dual boot.  I had installed the ati catalyst drivers.  I recently did a update through software center on some apps.  After rebooting I go to command line.  It won't boot to the GUI.  I've tried purging the flgrx file, reverting the xorg.conf file.  No luck.  I can't fix the issue.  I don't want to reinstall Ubuntu.  I'm very new at Ubuntu, can someone give me instructions to fix my machine?  Thanks

---

### Post by abyrne on 2012-08-22
First off, welcome to the forums!

Second, you might want to try a thread title that's a bit more descriptive next time. It will get more people to read your post.

Have you tried uninstalling the ATI drivers? At least you will be able to get a GUI. 

And what video card are you using?

---

### Post by apexone4697 on 2012-08-23
Thank you.  I've tried uninstalling the old ati drivers.  No luck.  I'm running ati mobility radeon HD 5400.  I think I messed up my xorg.conf file.  I can't run startx, it freezes.  It looks like there are still remnants of old catalyst install that I can't seem to completely get rid off

---

### Post by papibe on 2012-08-23
Thread title changed to '**help! no gui after software update**'.

---

### Post by MutantJohn on 2012-08-23
I had my GUI crash once. For me, I just had to create a new user account and the GUI returned. Something to do with the compiz settings or w/e being bound to that one user account so a fresh one gave me fresh settings. I say try it out.

---

### Post by Random20210831 on 2012-08-23
Are you installed latest graphics drivers for your graphics card? If you are not, uninstall old drivers and install latest drivers from official AMD site.

---

### Post by mastablasta on 2012-08-23
read and do the need to purge FGLRX section:
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver")

---

### Post by apexone4697 on 2012-08-23
I've read the wiki and typed all commands in to delete and purge old fglrx files.  When I enter commands in to start fresh install of ati fglrx, it stops and says there is a old installation that needs to be removed first.  I can't figure this out.  How do I delete this fglrx and revert to stock or propriety drivers?

---

### Post by Marqin on 2012-08-23
How have you installed your drivers? Via apt or some .tar.gz?

---

### Post by apexone4697 on 2012-08-23
I installed via command line through a posted how-to

---

### Post by NikTh on 2012-08-23
Hi , 
please write down to a paper (of via mobile photo) below commands and run them carefully in Console mode. (go to Console mode with Ctrl+alt+F2 and login with username and password). 

```
sudo sh /usr/share/ati/fglrx-uninstall.sh 
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* 
sudo rm /etc/X11/xorg.conf  
sudo apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core  
sudo dpkg-reconfigure xserver-xorg  
sudo reboot
```If first command gives an error , ignore it and proceed with others. 
******after libgl  it is 1 (number one) 

Thank you.

---

### Post by apexone4697 on 2012-08-24
So I attempted to do the commands.  After first cmd I get 'one or more files have been altered since installation. Uninstall will not be completed. See /etc/ati/fglrx-uninstall.log for details
The after the second command, I get a bunch of errors saying the packages are not installed so they are not removed.  At end it says '0 upgraded. 0 newly installed. 0 to remove and 4 not upgraded.
Then the next cmd tells me 'rm: cannot remove `/etc/x11/org.conf' no such file or directory.
Then last cmd says 'you should explicitly select one to install
E: package 'libgl1' has no installation candidate.

I'm stumped.  I've tried so many commands the last few days that I think I caused more damage.

---

### Post by NikTh on 2012-08-24
Hi , 
can you post the output of 
```
/etc/ati/fglrx-uninstall.log
```you can pass through the results  to a text file with this command 
```
cat /etc/ati/fglrx-uninstall.log >> uninstall.txt
``` 
and then we want the content of uninstall.txt 

Thank you.

---

### Post by apexone4697 on 2012-08-24
ok, so i got the problem fixed.  I installed the ati drivers though command my adding --force at the end.  Before it would open the installer and then freeze with a msg saying that there was a existing installation of drivers, and then it would quit.  So i got ubuntu to boot to gui.  now im trying to ensure the opensource drivers are enabled.  I get a error msg when i type fglrxinfo in prompt, so i think fglrx is gone.  But when i go to details in settings, and click graphics, it says something weird.  It used to say mesa, now it says something different.  Should it say mesa?  how do i take all these proprietary drivers out, and make it like it was when i first installed?  thanks for all your help guys!

---

### Post by NikTh on 2012-08-24
Hi ,
you can see what drivres you use with these two commands 

```
lspci -nnk | grep -iA2 vga
/usr/lib/nux/unity_support_test -p
```
Thank you.

---

