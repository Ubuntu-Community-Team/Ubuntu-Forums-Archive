---
title: "teamvier missing after reboot"
date: 2011-01-12
forum: General Help
---

### Post by joesto1 on 2011-01-12
hi all
i installed a program which works great but if i reboot the pc it is not listed in 
applications-internet
where is was before the reboot
if i go to terminal and run it it works ok so!!
1 how do i make it insatll propely 

2 how do i make it auto run from reboot
thanks
joe
ps i usr ubuntu 10.04:D

---

### Post by howefield on 2011-01-12
Thread moved to General Help.

For me the menu item shows on install, but a reboot makes it disappear. So it needs manually adding as a menu item.

Go to System > Preferences > Main Menu and create the launcher.

Normally you would create the launcher for Teamviewer in the Applications > Internet menu, but place it wherever you want.

The details you will need for each field are as follows.

Name/Description : Teamviewer
Command : /opt/teamviewer/teamviewer/5/bin/teamviewer
Comment : TeamViewer Remote Control Application

Click on the "springboard" icon, and navigate to /opt/teamviewer/teamviewer/5/desktop for the proper icon.

Job should be done.

---

