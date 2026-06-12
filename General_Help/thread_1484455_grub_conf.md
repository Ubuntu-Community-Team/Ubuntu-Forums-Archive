---
title: "grub conf"
date: 2010-05-15
forum: General Help
---

### Post by unplugged23 on 2010-05-15
Hi all,

On and off for a little while now, I've been struggling to get a clean install of 10.04. I have finally accomplished this task, but my only issue now is that with every reboot of the system, I have to enter the grub menu, so I can add 'nomodeset' to the end of the boot line, to get X to launch without going out of range. I figured this would be easy, and I ran 'sudo nano /boot/grub/menu.lst' which turns out, does not exist. It put me in a brand new file.

Am I trying to go to the wrong place, or is there a good template somewhere, that I could paste in?

Thanks guys! :)

---

### Post by vivien` on 2010-05-15
Grub has been replaced by Grub2. Search for details about Grub2 on the web. For instance:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by unplugged23 on 2010-05-15
Thanks, look like I got this solved. I ran 'sudo update-grub' which should save my settings. I'll mark this solved if it works after a reboot.

RIP grub 1, I'll miss it's editable-ness forever! :(

---

### Post by angry_johnnie on 2010-05-15
i know you've nailed this one, but just in case you're interested, given you'll miss (like so many others) grub legacy's editable-ness forever :p

you could just

sudo chmod a+w /boot/grub/grub.cfg

and then

gksu gedit /boot/grub/grub.cfg

edit & save the file

of course the next update-grub will hose it, but then it's a lot easier editing just one file, or at least that's my opinion.

it's quick and dirty, yes, but it works :p

---

