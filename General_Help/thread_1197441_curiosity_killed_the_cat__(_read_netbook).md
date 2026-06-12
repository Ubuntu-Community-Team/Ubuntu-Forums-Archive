---
title: "curiosity killed the cat  ( read netbook)"
date: 2009-06-26
forum: General Help
---

### Post by juliancam on 2009-06-26
I am running the 9.04 netbook version on an acer 110 SSD and did something stupid. I have managed to kill my panels. I came across this setting to change the display from netbook to classic and of course being me I just had to click on it. It all seemed to go fine until I tried to switch back to netbook display at which time it warned that some files couldn't be loaded but everything seemed to be working fine. However on the next boot I got the same warning with the added message that this may be due to some broken files. It continued to load but no panels came up just the icon for the sd card I have in the expansion port. If I click on that a window comes up locked to the bottom left of the screen. From there I can get to firefox and vlc and they work. It even did an automatic update so it seems to be just the panels.

Now I am a comparative newbie but looking at other posts I have tried sudo /etc/init.d/gdm restart from <ctl> <alt> <f1> to no effect - well I now have an untitled folder on the screen as well as the sd card icon. 

My question is: With all my data stored seperately on the SD card is it better to reinstall and go through all the updates and loading VLC etc or is there a fix that I might be able to follow?

Thanks 

Julian

---

### Post by Thingymebob on 2009-06-26
hit alt + f2 in the box type gnome-panel
Should get you at least an empty panel from which you can rebuild yours.

if it doesn't, backup then delete everything under /home/username/.gconf/apps/panel/ and /home/username/.gconf/apps/gnome-settings/gnome-panel and try again

---

### Post by juliancam on 2009-06-26
Sorry Thingymebob, but is that "hit alt f2 in the box" or "hit alt f2" and then in the box type... as in the first there is no box for me to press alt f2 in - when in ctl alt f1 it has no effect- and in the second <alt>-<f2> has no effect? Also searching in the Nautilus window that opens when I click on the SD card reveals no .gconf in the folder home/julian. (edit: oops I did not have show hidden files checked, I can see it now however I cannot get to panels in apps due to the locked position of the window and gnome-settings does not have a gnome-panel in it). 

Whilst I am a stubbon S.O.B.,  re-installing is beginning to sound like a good option. I think I am just to much of a newbie at this stage.

J

---

### Post by Thingymebob on 2009-06-26
sorry, when at your crippled desktop, press alt+f2, then in the box that pops up....

---

### Post by Brandon Williams on 2009-06-26
Alt-F2 will have no effect if you have no panels, since the run dialog is a function of gnome-panel.

The bug you are experiencing is in the [release notes](http://www.ubuntu.com/getubuntu/releasenotes/904#Missing%20GNOME%20panels%20in%20Ubuntu%20Netbook%20Remix%20after%20using%20the%20desktop-switcher%20application) and the [known jaunty bugs](http://ubuntuforums.org/showpost.php?p=7253643&postcount=15) list. Check there for the fix. A new desktop-switcher package is in the jaunty-proposed repository and should be making its way to updates soon.

---

### Post by Thingymebob on 2009-06-27
> **Brandon Williams said:**
> Alt-F2 will have no effect if you have no panels, since the run dialog is a function of gnome-panel.
Didn't realise that! Thanks Brandon.

---

