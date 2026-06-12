---
title: "help with openSUSE anyone?"
date: 2011-04-18
forum: General Help
---

### Post by poodoopealeoaph on 2011-04-18
Alright, so, as with all of the ubuntu 11.04 derivatives, there is no backlighting when I try to install openSUSE 11.3 and 11.4. I read that if you select nomodset at the beginning of installation it will allow you to install without the backlighting cutting out. Well, no matter how I try to select nomodset in the installer, it won't work. I tried this method in trying to install Kubuntu 11.04 beta 2 and it worked fine for install but after I restart the computer, the backlighting is gone again. So... I need help trying to get nomodset to be accepted in the openSUSE installer and also, in either ubuntu or openSUSE, how do you get nomodset to automatically run when you start up?

oh and is this just a bug that is happening with the new linux kernel? i sort of figure it must be since it is happening on every linux distro with the new kernel....

---

### Post by Quackers on 2011-04-18
If you needed the nomodeset option to install, you will need to use it again the first time you boot the new installation (kubuntu). If you have installed grub2 you should hold down the shift key whilst booting to bring up the grub menu.
When the menu appears the top item should be your kubuntu system and it should be highlighted. If so, press the "e" key.
On the next screen using the arrow keys navigate to the end of the kernel line, which currently ends with "quiet splash". At the end of quiet splash press the space bar then type in "nomodeset" (but without the quotes) then press ctrl + X to boot.
When the desktop loads you should get a prompt to install graphics drivers. Install them, then booting should be ok.
If you don't get a prompt to install video drivers go to System > Admin > additional Drivers

openSUSE has completely different methods for installing video drivers. The openSUSE forum may be more help to you.

---

### Post by poodoopealeoaph on 2011-04-19
oh wow, I was dumb enough that I actually thought it was "nomodset" instead of "nomodeset"... so I tried typing "nomodeset" before i selected install for the openSUSE install and it worked. the only thing is that the installer was really confusing and by the time I got to the point to actually install I realized that I didn't want to give it a chance. It had been quite a while since I've had a fresh install of Ubuntu 10.10 anyway so I put that back on my system and decided to actually keep it looking and behaving the way it does out of the box instead of customizing the crap out of it and I realized something. Ubuntu is perfect as is and if you keep things as is, your system will completely rape! my computer is so much faster than it was by far! I'll probably just sit back for the final release of 11.04 and see how it goes with people fixing the backlighting problems. After everything is settled I'll upgrade but as for now I'm happy!

---

