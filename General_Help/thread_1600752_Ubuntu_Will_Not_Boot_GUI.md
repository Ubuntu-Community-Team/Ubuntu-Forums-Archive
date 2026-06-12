---
title: "Ubuntu Will Not Boot GUI"
date: 2010-10-19
forum: General Help
---

### Post by Tomination on 2010-10-19
Hi i have Ubuntu 10.10 installed on my external hard disk, works great in my laptop but on my computer it never boots into the GUI. For example; it goes to a black screen and asks me to login like a command line terminal.

I dont know how to get my pc to boot ubuntu into the normal system, can you help? 

PS: i am new to linux, so please provide explanations for the terminology :D

---

### Post by oldfred on 2010-10-19
It issue is probably a different video card and it is not correctly set up.

On first boot after install, press e on getting the GRUB bootloader menu.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

If you want to then boot from portable you may have to reverse settings for video driver.

I have not used this:
use the uvesafb to fix all the problems
[http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/)

Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

---

### Post by Tomination on 2010-10-20
@Oldfred

I changed the bit from quiet splash to nomodeset and pressed CTRL + X

But it didnt boot even then, loads ot text started to write checking parts of the system (something failed but i couldnt see what) and then it prompted me to login via the command line style thing again

When i login it just says some technical stuff and then gives me the URL for Ubuntu Documentation

---

### Post by lisati on 2010-10-20
What happens if you log in and type the following?
> startx

---

