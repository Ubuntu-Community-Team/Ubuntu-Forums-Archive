---
title: "Screen Size Issue"
date: 2012-04-04
forum: General Help
---

### Post by jacob70 on 2012-04-04
So, i have a screen slightly larger then the norm, it's 32 In. I remember when i first started using this screen we had to do a bit of fixing up to get it to work correctly. 

When I use Ubuntu, a lot of the screen is cut off of the sides, and I found where to change the screen resolution, but no matter what i tried they all pretty much made it swell up to where i couldn't even see what i was seeing before.  

How do I fix this? I really love Ubuntu, but this kills me.

Secondly, It said I wasn't getting internet connection when i first started it. Is this normal, because im new i just simply dont know. If it's normal how do i establish a connection?

---

### Post by papibe on 2012-04-04
Hi again jacob70 ):P

Could you post the result of these commands to determine the exact graphic card brand and model?
```
lspci | grep -i vga

sudo lshw -C display
```
Also there are a couple of file that can gives some clues. Paste them here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post back the link:
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Regards.

---

### Post by efflandt on 2012-04-04
For some reason Linux has difficulty determining optimum screen resolutions using VGA, and if possible, DVI (or HDMI) would likely more easily determine the proper native resolution.  I am currently using a DVI to HDMI cable for my 32" 1080p HDTV (and have also used straight HDMI), but my LG TV has a mode called "Just Scan" which tries its best to show whatever it receives full screen, and works better automatically 1920x1080 than if I simply set the TV to 16:9.

As far as the internet connection, do you have a wired (ethernet) connection using DHCP to assign IP address or wireless? The former should be pretty much automatic.  If wireless I think if you right click on the network applet it should show available wireless AP's, but you would need to enter whatever key (WEP, WPA, etc.) for that connection (or set up the connection if using something like mobile data, direct PPPoE on your computer if your modem does not handle that, etc.).

---

### Post by jacob70 on 2012-04-05
I already know my graphics is a Nvidia GeForce GT 430. Is that what you need to know? I am also using and HDMI connection from the computer to the screen. Also, I get my internet wirelessly.

---

