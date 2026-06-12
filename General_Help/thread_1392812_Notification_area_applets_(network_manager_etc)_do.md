---
title: "Notification area applets (network manager etc) don't start at boot"
date: 2010-01-28
forum: General Help
---

### Post by GSMX on 2010-01-28
Hi,

I had some problems lately with bootup, so I powered my laptop off with the hardware button during boot several times. That boot problem is gone, but another problem came: Applets in the notification area are not started anymore. 

To use them I have to manually give the commands
'nm-applet'; 'gnome-volume-control-applet'; 'bluetooth-applet'; 'ubuntuone-client-applet'

But also 'gnome-do' doesn't start anymore.

All those programs are still in the list of system->preferences->startup applications

How can I get them to start at boot again?

---

### Post by GSMX on 2010-01-30
*bump*

---

### Post by Aimetal on 2010-01-30
Hi GSMX,

I installed Karmic about a week ago and just today my network manager disappeared along with the 
volume control from the top panel. I'm also forced to manually start the network manager via using
ALT-F2 then typing in 'nm-applet --sm-disable' , this gets my WiFi network connection back but shouldn't have to do it this way. I also noticed that sound output is always muted after boot and the screen saver doesn't run anymore. I'm wondering if applications in the 'Startup Applications' aren't
being run at boot time. I know this probably doesn't help you. I have been searching on forums and others are having similar problems. I'll post again if I find anything  usefull. 
Cheers.

---

### Post by garvinrick4 on 2010-01-30
> **GSMX said:**
> Hi,

I had some problems lately with bootup, so I powered my laptop off with the hardware button during boot several times. That boot problem is gone, but another problem came: Applets in the notification area are not started anymore. 

To use them I have to manually give the commands
'nm-applet'; 'gnome-volume-control-applet'; 'bluetooth-applet'; 'ubuntuone-client-applet'

But also 'gnome-do' doesn't start anymore.

All those programs are still in the list of system->preferences->startup applications

How can I get them to start at boot again?
It is still added in right click toolbar/add to panel/notification area

---

### Post by Aimetal on 2010-01-30
> **GSMX said:**
> Hi,

I had some problems lately with bootup, so I powered my laptop off with the hardware button during boot several times. That boot problem is gone, but another problem came: Applets in the notification area are not started anymore. 

To use them I have to manually give the commands
'nm-applet'; 'gnome-volume-control-applet'; 'bluetooth-applet'; 'ubuntuone-client-applet'

But also 'gnome-do' doesn't start anymore.

All those programs are still in the list of system->preferences->startup applications

How can I get them to start at boot again?
Hi,
Regarding manual start of applications I have been having problems with booting Karmic. Sometimes
GRUB starts then the white UBUNTU logo appears centre screen for the normal amount of boot time.
After the logo disappears I just get a black screen and the mouse and keyboard are dead, have to 
reboot with the power button. The reboot usually works although this is annoying.
This brings me to the missing applications in the Notification Area. During the previous few days
while trouble shooting the boot problem I had selected 'Failsafe GNOME' at the bottom of the UBUNTU log on screen and forgotten to reselect 'GNOME'. 'Failsafe Gnome' must ignore startup preferences, this makes sense if you think about it. Now the WiFi and volume control are back on the top panel and the screen saver runs again. Now I just have to solve the boot to black problem, this may just be a problem between my hardware platform and UBUNTU 9.10. Will post an update on this if I find/fix anything.

---

### Post by Pizarro on 2010-01-31
Same problem I've just lost network,bluetooth and volume from the bar.

"It is still added in right click toolbar/add to panel/notification area"   sorry just re-read this thread and checked and i had re-moved this in error

---

### Post by GSMX on 2010-02-01
> **Aimetal said:**
> Hi,
Regarding manual start of applications I have been having problems with booting Karmic. Sometimes
GRUB starts then the white UBUNTU logo appears centre screen for the normal amount of boot time.
After the logo disappears I just get a black screen and the mouse and keyboard are dead, have to 
reboot with the power button. The reboot usually works although this is annoying.
This brings me to the missing applications in the Notification Area. During the previous few days
while trouble shooting the boot problem I had selected 'Failsafe GNOME' at the bottom of the UBUNTU log on screen and forgotten to reselect 'GNOME'. 'Failsafe Gnome' must ignore startup preferences, this makes sense if you think about it. Now the WiFi and volume control are back on the top panel and the screen saver runs again. Now I just have to solve the boot to black problem, this may just be a problem between my hardware platform and UBUNTU 9.10. Will post an update on this if I find/fix anything.


Thank You!
I remembered now that I also selected Failsafe Gnome and never changed it back. A moment ago I changed it back again and now all applets are started again.

My issues are solved.

---

