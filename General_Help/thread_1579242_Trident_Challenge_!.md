---
title: "Trident Challenge !"
date: 2010-09-21
forum: General Help
---

### Post by Cpierce on 2010-09-21
Alright, I need the Ubuntu Masterminds. 

I am putting Ubuntu on an old HP XH455 laptop which has a Trident Cyberblade XP card. Because of the slow processer and small RAM, I chose Lubuntu. The issue is that the maximum resolution is 800x600 when it should be 1024x768. So I am left with a small desktop on a big screen that has an inch of blank/black border all the way around. If I run "xrandr" it shows that it sees a max of 800x600, instead of the 1024x768. I checked the package manager and the trident 1.3.3-1 driver is installed. 

I have read a bunch of posts, but most all of them are about xorg. I don't believe Lubuntu uses xorg. To get rid of the black box around cairo-dock, I installed xcompmgr. Then ran"sudo gedit /etc/X11/xorg.conf". I believe it must have created an xorg.conf file because it was empty. I added :

Section "Extensions"
                Option "Composite" "Enable"
        EndSection

to the xorg.conf and saved it. I rebooted and compositing works, so I guess the xorg file could be used. But I don't believe this is the right way to do this. I should be adding "compositing and modifying the .cong file that Lubuntu is actually using. 

The display was 1024x768 when windows was installed, and I had this same "small 800x600 desktop" issue when I tried Ubuntu 10.04 and Peppermint. I should note that the startup screens do show as fullscreen, it is only when the desktop starts that it is small. I did check the BIOS and expanded display was enabled. 

Can someone please help ?

---

### Post by Joe of loath on 2010-09-21
Lubuntu uses xorg, in fact I think every graphical Linux distribution uses it.

Try some of the xorg solutions, see how they go.

---

### Post by Cpierce on 2010-09-21
Thanks for the info. I thought it used something different than xorg. I know it uses openbox and the display manager is LXDM. Why would the xorg.conf file be empty ? I did try a xorg fix, which locked up the laptop. I had to boot on the live CD and undo the changes. However from what I have read, you can create an xorg.conf file which will over-ride the the other settings. I saw another xorg fix that I am going to try, hopefully it will work. I still believe there must be another conf file that I could change, but I am still a newbie so I don't know.

Again, appreciate the help

---

### Post by Cpierce on 2010-09-22
I got it solved. I tried the other xorg fix and it worked. Here is the post that helped me:

[http://ubuntuforums.org/showthread.php?t=806835](http://ubuntuforums.org/showthread.php?t=806835)

I did change the two places in the script that listed "Trident Microsystems CyberBlade XPAi1" to "Trident Microsystems CyberBlade XP" since I have the XP card not the XPAi1 card.

---

