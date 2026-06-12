---
title: "Grub issues.."
date: 2010-08-15
forum: General Help
---

### Post by The Living Shadow on 2010-08-15
Hi, I am new so if I have posted in the wrong section I apologize in advance.

recently, I took under the task of attempting to place a background image on the GRUB2 boot screen. I followed these the following two guides and have seemed to have missed something in the process.

Guide [one]("https://wiki.ubuntu.com/Grub2#Background%20Colors/Image") was placed on the ubuntu wiki, whereas guide [two]("http://ubuntuforums.org/showthread.php?t=1195275") was placed on the forums.
I am, not exactly sure where I might have taken a wrong turn so I have taken the liberty to upload my grub.d folder in a .tar archive, but can re-upload if there is a problem.

also, as a side note, since I have attempted to change my Grub2 background, I am unable to install anything from the ubuntu software center, or for that matter, any .deb files downloaded from the Internet.

here is the output:

Package operation failed.
the installation or removal of the package has failed.
```
installArchives() failed: Selecting previously deselected package alarm-clock. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 158518 files and directories currently installed.) 
Unpacking alarm-clock (from .../alarm-clock_1.2.5-1_i386.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for man-db ... 
Processing triggers for menu ... 
Processing triggers for python-support ... 
Setting up ubuntu-splash-image (1.1) ... 
Generating grub.cfg ... 
basename: missing operand 
Try `basename --help' for more information. 
basename: missing operand 
Try `basename --help' for more information. 
No path or device is specified. 
Try `/usr/sbin/grub-probe --help' for more information. 
No path or device is specified. 
Try `/usr/sbin/grub-probe --help' for more information. 
dpkg: error processing ubuntu-splash-image (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up grub-ieee1275 (1.98-1ubuntu7) ... 
Generating grub.cfg ... 
basename: missing operand 
Try `basename --help' for more information. 
basename: missing operand 
Try `basename --help' for more information. 
No path or device is specified. 
Try `/usr/sbin/grub-probe --help' for more information. 
No path or device is specified. 
Try `/usr/sbin/grub-probe --help' for more information. 
dpkg: error processing grub-ieee1275 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up alarm-clock (1.2.5-1) ... 
 
Processing triggers for menu ... 
Errors were encountered while processing: 
 ubuntu-splash-image 
 grub-ieee1275 
Setting up grub-ieee1275 (1.98-1ubuntu7) ... 
Generating grub.cfg ... 
basename: missing operand 
Try `basename --help' for more information. 
basename: missing operand 
Try `basename --help' for more information. 
No path or device is specified. 
Try `/usr/sbin/grub-probe --help' for more information. 
No path or device is specified. 
Try `/usr/sbin/grub-probe --help' for more information. 
dpkg: error processing grub-ieee1275 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up ubuntu-splash-image (1.1) ... 
Generating grub.cfg ... 
basename: missing operand 
Try `basename --help' for more information. 
basename: missing operand 
Try `basename --help' for more information. 
No path or device is specified. 
Try `/usr/sbin/grub-probe --help' for more information. 
No path or device is specified. 
Try `/usr/sbin/grub-probe --help' for more information. 
dpkg: error processing ubuntu-splash-image (--configure): 
 subprocess installed post-installation script returned error exit status 1
```I apologize for any trouble i may have caused  and greatly appreciate any and all help given.

yours kindly,
      --The Living Shadow.

---

### Post by The Living Shadow on 2010-08-16
*bump*

---

### Post by The Living Shadow on 2010-08-16
bump one more time, seems the topic hasn't moved on the forum.

---

### Post by The Living Shadow on 2010-08-16
bump

---

### Post by john newbuntu on 2010-08-16
I took a look at you tar file. I am assuming that these files are all located in /etc/grub.d/.  Get rid of files that start with '05_debian_theme.' (or better, move the files to another directory) except 05_debian_theme.  For the time being move the 06_ubuntu_theme also out of the way.  Make sure the file /home/andrew/grubimg/conan.png exists.

Then run "sudo update-grub" from the terminal. See if this helps.

---

### Post by The Living Shadow on 2010-08-17
> **john newbuntu said:**
> I took a look at you tar file. I am assuming that these files are all located in /etc/grub.d/.  Get rid of files that start with '05_debian_theme.' (or better, move the files to another directory) except 05_debian_theme.  For the time being move the 06_ubuntu_theme also out of the way.  Make sure the file /home/andrew/grubimg/conan.png exists.

Then run "sudo update-grub" from the terminal. See if this helps.

thank you so very much for your help.

it would that seem to have fixed the install issues, I was able to install a few test packages.
but when i go  to run:
```
sudo update-grub
```it freezes after listing the two kernels i have listed, actually the whole computer freezes.


when i hard reboot, it lists the two kernels but does not show the picture.


edit: i was able to resolve the freezing problem, i went and edited the 05_debian_theme, where it says use_bg= the first time, it said true on the first one and false on the second one, i corrected it by typeing in false. but i still have no background splash on grub. 

thank you for all the help.:D

---

### Post by john newbuntu on 2010-08-18
I am not sure on the exact solution to your problem.  I'd suggest not messing with 05_debian_theme inititally and just using the default one (the one in your tar file) with the wallpaper variable change.  But here are a few harmless things you could try:

1.  Check if the file /boot/grub/png.mod exists.
2.  The obvious - make sure that you are able to open and view the .png file and is fairly big (-just to test- not at all a requirement.  But mine is 1920X1200 pixels!!)
3.  Copy your conan.png file to /usr/share/wallpapers directory.  Make root the owner and make the file readable. i.e,  sudo cp ~/conan.png /usr/share/wallpapers/
4.  Make the appropriate change to the "WALLPAPER" variable in /etc/grub.d/05_debian_theme
5. sudo update-grub. (Now when you do this, it should say "Found background image: ...".  

If the hang still persists, try disabling os-prober as drs305 has pointed out here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) and rerun sudo update-grub.

If none of these solve your problem, I am out of ideas.  Please undo your changes.

---

### Post by The Living Shadow on 2010-08-18
> **john newbuntu said:**
> I am not sure on the exact solution to your problem.  I'd suggest not messing with 05_debian_theme inititally and just using the default one (the one in your tar file) with the wallpaper variable change.  But here are a few harmless things you could try:

1.  Check if the file /boot/grub/png.mod exists.
2.  The obvious - make sure that you are able to open and view the .png file and is fairly big (-just to test- not at all a requirement.  But mine is 1920X1200 pixels!!)
3.  Copy your conan.png file to /usr/share/wallpapers directory.  Make root the owner and make the file readable. i.e,  sudo cp ~/conan.png /usr/share/wallpapers/
4.  Make the appropriate change to the "WALLPAPER" variable in /etc/grub.d/05_debian_theme
5. sudo update-grub. (Now when you do this, it should say "Found background image: ...".  

If the hang still persists, try disabling os-prober as drs305 has pointed out here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) and rerun sudo update-grub.

If none of these solve your problem, I am out of ideas.  Please undo your changes.

Hello again, and thank you for attempting to help me in my ordeal,

i just want to verify that the command
```
sudo update-grub
```no longer freezes the computer, as i have stated in my recent edit.

as for your list of suggestions,
#1. yes the files does exist.
#2. yes the file opens and displays fine.
#3. i used the command
```
sudo nautilus
```to navigate through and relocate the file.
#4. the changes where made and,
#5. i ran the code and this is what the terminal printed.
```
andrew@andrew-netbk:~$ sudo update-grub
[sudo] password for andrew: 
Generating grub.cfg ...
Found background image: conan.png
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
done
andrew@andrew-netbk:~$ 

```i then ran the following command
```
sudo reboot
```buy when grub appeared, the picture did not display, would you like me to re archive my grub.d folder and upload it so you may take a look?

---

### Post by john newbuntu on 2010-08-18
Please post the /boot/grub/grub.cfg and /etc/default/grub files in code tags.  Yours appears to be a single OS system. If not me, someone else might be able to help.

---

### Post by The Living Shadow on 2010-08-18
> **john newbuntu said:**
> Please post the /boot/grub/grub.cfg and /etc/default/grub files in code tags.  Yours appears to be a single OS system. If not me, someone else might be able to help.

i have just realized, 

i forgot to switch en_bg=false to en_bg=true](*,)

thank you for your help, i rebooted and all is well!

now, im going to go hide under a rock:lolflag:

---

