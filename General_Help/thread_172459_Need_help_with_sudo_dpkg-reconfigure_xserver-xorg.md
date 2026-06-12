---
title: "Need help with sudo dpkg-reconfigure xserver-xorg"
date: 2006-05-08
forum: General Help
---

### Post by cooldudejz on 2006-05-08
i just changed out my video card for a nvidia GeForce 7300GS in ubuntu 5.10, so i had to run sudo dpkg-reconfigure xserver-xorg. after i do all of this it says it overwrote the config and made a backup. i then do a sudo reboot, and reboot my computer only to find out that none of the config i just did svaed and i have to do it all over again, except it never gets saved. i am writing this email from ubuntu 6.06 beta, my graphics card working perfectly by the way. do i need to download some drivers or something, i dont understand why it wont save my new configs. thanx

---

### Post by Nano Geek on 2006-05-08
In the command line, try typing ```
sudo vi /ect/X11/xorg.conf
``` Then go down to the section called device, and change the **Driver** name to **nv**, and press **Esc** and type **:x**. After that restart and that should fix it.

---

### Post by daldous on 2007-09-01
> **asjdfwejqrfjcvm msz34rq33 said:**
> In the command line, try typing ```
sudo vi /ect/X11/xorg.conf
``` Then go down to the section called device, and change the **Driver** name to **nv**, and press **Esc** and type **:x**. After that restart and that should fix it.

Just a quick question here: I have a 6800GS from nVidia and vesa wouldn't give me 1680x1050 with the "sudo dpkg-reconfigure -phigh xserver-xorg" (I tried restarting the comp, highest I could get was 1280x1050) so I changed vesa to nv in the config file. Well, whoops. After the load screen for ubuntu, I get the following neat message from my monitor (not software):

Analog
Out of Range
35.4kHz / 78 Hz

Any ideas on how to fix that? I can't get into ubuntu itself in order to modify that config file -- am I screwed?

My monitor is flat and 22 inches wide. It's made by LG and I can't remember the exact make but I could find the box downstairs if need be. I'd really love it if I could see ubuntu at 1680x1050 (the native resolution for the monitor) -- can ya'll offer some advice? 

I've also tried installing Fedora and I would get the same problem with the graphical installer. Come to think of it, same happened with ubuntu -- the Out of Range message would pop up during the graphical installer. I had to use the text installer for Ubuntu ... which turned out to be graphical and very easy :)

Any help ya'll can offer would be more than appreciated.

---

