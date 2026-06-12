---
title: "Can someone help me install this nVidia graphics driver?"
date: 2011-11-29
forum: General Help
---

### Post by MutantJohn on 2011-11-29
Hello Ubuntu Community,

I have an nVidia GeForce GTX 460 and I'm using their kernel module 280.13 and I'd like to use a more recent one from their website that's not recognized by Ubuntu's Additional Drivers in the System Settins. The kernel module is 285.05.09 and every time I try to run it it says that I need to end my X session. Or that there's an X session still running.

Basically, I think I need to kill my graphics processes temporarily so that I can run and install the new driver. I've looked this up before and saw a bunch of commands like pkill gdm or for me it was service stop gdm, I think. But none of these really worked or did anything which was lame.

And I just checked, if I type in "stop gdm" I get, "stop: Unknown instance:"

Can anyone help me out here? I'd like to be running this with fancy graphics. Thank you in advance, anyone that tries to help.

---

### Post by efflandt on 2011-11-29
I believe that 11.10 with Unity uses **lightdm** instead of **gdm**, but **sudo service lightdm stop** makes my screen in the console go bonkers, and for some reason there is no returning to X from the console (Alt+F7) with nvidia (at least for me) even if it is still running (completely lose video signal and cannot even get back to console).

Just do this in a terminal:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```Then with **Update Manager**, **Check** for updates and install, and you will end up with nvidia 290.10 drivers that "should" work with Ubuntu.

I and some others have been having some issues with any nvidia drivers (screen freeze) in Ubuntu 11.10, while same drivers work fine in Maverick (I have had x-swat set up in that for some time from when I was configuring HDMI audio to work before older drivers supported that). But I may have some other video hardware issue because nvidia often leaves the bus during boot (totally lose video signal between grub menu and login screen) and I also started having screen freeze in Win7, so I am going to try a different video card.

---

### Post by MutantJohn on 2011-11-30
Thank you, thank you, thank you. You've finally helped me accomplish what I could not for so long. Now I feel so fancy using using the 290.10 drivers. 

Although I must say, I haven't actually had any weird hiccups with Ubuntu and my graphics card. Maybe you're card is just too advanced for Ubuntu?

---

