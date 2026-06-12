---
title: "(Ubuntu 10.04) Text console is too large for the screen"
date: 2010-05-12
forum: General Help
---

### Post by marinuso on 2010-05-12
I have installed Ubuntu 10.04 server on my Tulip Topline 300P laptop, and it is using 80x30 as a default TTY size instead of 80x25. This is annoying, because I can't see the last five lines on the screen. I can temporarily fix it using "stty rows 25", but that only works when I'm logged in and I have to do it every time I do so. 

It did this even during the installation, though the screen where you enter the boot options was OK. When installing, disabling the frame buffer had no effect on the screen size even though the font did change so it did actually disable the frame buffer, and adding "vga=771" as the help said to do for laptops with display problems just gave a blank screen instead of the installer. The installed system has the same problem.
 
I used to have Ubuntu 8.10 server on this machine, and that did not give me any problems. I just did a clean install of 10.04. 

I also found [this archived thread](http://ubuntuforums.org/showthread.php?t=125291) where someone seems to have the exact same problem I have. He was told to do "stty rows 25", but again no permanent solution was offered.

I don't want to put "stty rows 25" in .profile or /etc/profile, because that would make SSH-ing into the machine very awkward, apart from being an ugly hack. When using SSH there are no problems with detecting the terminal size, though of course I shouldn't expect any there.

tl;dr: how do I convince Ubuntu my screen is (the standard) 80x25 instead of the 80x30 it's defaulted on?

---

