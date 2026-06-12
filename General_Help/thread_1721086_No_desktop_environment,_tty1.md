---
title: "No desktop environment, tty1"
date: 2011-04-04
forum: General Help
---

### Post by Wgimson on 2011-04-04
I'm an absolute Ubuntu noob. I installed 10.10 a couple days ago, and was happily playing with it. I wanted enable some of the cool 3D desktop effects, so i attempted to configure my NVidia graphics card with the command 'sudo NVidia-xconfig'. To the best of my recollection, that was the last thing I did before I shut down the system. The next day, after starting up, I find the tty1 screen in place of my graphical desktop. I can login, but after that I have no clue what to do. I've perused some of the other threads with similar subject matter, and tried some of the commands suggested. For whatever it's worth...

-sudo chmod a-x /usr/bin/compiz  
....gives me "Cannot access, no such file or directory"

-sudo dpkg-reconfigure xserver-xorg
   -sudo reboot
.......brings me right back to the tty1 screen

-sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
   -sudo apt-get update
      -sudo apt-get upgrade
......after these I'm right back where I started

-lsb_release -a
....after this I get "no lsb module available", and then some basic information about 10.10

- sudo service gdm start
.....gives me "start:job is already running:gdm"

That's all I've tried so far and I have no idea what any of it means. Any help would be very much appreciated.

---

### Post by TeoBigusGeekus on 2011-04-04
Delete your xorg file
```
sudo rm /etc/X11/xorg.conf
```
Reboot
```
sudo reboot
```
and when (if) you get into a working desktop, run 
```
gksu nvidia-settings
```
from terminal to configure your graphics.

---

### Post by Wgimson on 2011-04-04
Would I need to dpkg-reconfigure xserver-xorg before I reboot?

---

### Post by TeoBigusGeekus on 2011-04-04
No. Just reboot.

---

### Post by Wgimson on 2011-04-04
Ok, thanks a lot, I'm going to try now.

---

### Post by Wgimson on 2011-04-04
Worked like a charm. Thanks, Teo. :)

Now, however, when I entered "sudo nvidia-xconfig" after rebooting, I got....

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'


Any suggestions for this one?

---

### Post by TeoBigusGeekus on 2011-04-04
What is says exactly: you've deleted your xorg.conf file, so a new one was generated - which is what we wanted.

Do your changes and don't forget to click on "Write changes to xorg.conf" button (or something) after you're done.
It will ask you if you want to merge the changes with the existing configuration; answer yes.

---

### Post by wolfgangmcq on 2011-04-04
It couldn't find the file because you deleted the file. The first time you do that, it should report it can't find it. If it happens again, you *might* want to start getting worried.

---

### Post by Wgimson on 2011-04-04
.

---

### Post by Wgimson on 2011-04-05
Ok, so Teo's advice worked and I'm back in the desktop, but when I run
           gksu nvidia-settings
........I get "You do not" appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.", and I can't activate animations in compizconf. Or, more accurately, the window claims that animations are activated, but none of them are actually working.

When I ran 'sudo nvidia-xconfig' and restarted the X server with '
sudo /etc/init.d/gdm restart....I ended up in the same position that prompted me to make this post in the first place. A tty1 screen with no desktop, and a message reading...

PulsedAudio configured for per-user session
saned disabled; edit /etc/default/saned
* enabling additional executable binary formats binfmt-support
* checking battery state

The above message just stayed on the screen until I hit Ctrl+Alt+Del, and then I was taken to tty1 and had to run 'sudo rm /etc/X11/xorg.conf              sudo reboot' again to get my desktop back. Again, any help would be very much appreciated

---

### Post by Wgimson on 2011-04-08
bump............any help would be amazing, it's sorely needed.

---

