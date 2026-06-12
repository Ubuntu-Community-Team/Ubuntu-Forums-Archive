---
title: "Ubuntu 10.04 - Touchpad not working after last night's updates."
date: 2010-05-10
forum: General Help
---

### Post by TDK800 on 2010-05-10
It's not possible to select a thread prefix and post a new thread with no mouse/touchpad working, so could someone post this as a separate thread:

Title: Ubuntu 10.04 - Touchpad not working after last night's updates.

Message: Dell 1510 - touchpad not working, touchpad buttons neither, after last nights upate. Any suggestions?


Thanks

---

### Post by Orcie on 2010-05-16
Same problem here.

Asus ul30

---

### Post by Ofloo on 2010-05-16
same problem, and if i press the touchpad off button keyboard doesn't work either anymore.

---

### Post by seniortaco on 2010-05-17
I'm not sure if this is related to my case. My touchpad went out recently and I've got no idea why. I've plugged in a usb mouse and now that seems to work but the touch pad shows up it just doesn't do anything.
I'm not sure whats caused it, perhaps it was an update? Here's a link if anyone wants to look into it. [http://ubuntuforums.org/showthread.php?t=1485443](http://ubuntuforums.org/showthread.php?t=1485443)

---

### Post by Hopper122 on 2010-05-19
Found a fix that worked for me.  I am using a HP Pavilion dv9000 touch pad stopped working but a USB mouse would work fine.  Also my touch pad would work in KDE but not in Gnome...  So either install KDE and use it or...

Create a file called 
/etc/modprobe.d/touchpad.conf

You can do this by typing 
sudo gedit /etc/modprobe.d/touchpad.conf
in your terminal (Applications --> Accessories --> Terminal).  It will ask for your password

when the file opens put in it
options psmouse proto=imps 
Save the file and restart.

Hope this works for you  :P

---

### Post by Elmer Fudd on 2010-05-23
Thanks. That got my touchpad working past the login screen. Touchpad still will not toggle back on after using hardware switch to turn it off.

Acer 7736Z-4809
Ubuntu 10.04

---

### Post by hopugop on 2010-06-04
> **Hopper122 said:**
> Found a fix that worked for me.  I am using a HP Pavilion dv9000 touch pad stopped working but a USB mouse would work fine.  Also my touch pad would work in KDE but not in Gnome...  So either install KDE and use it or...

Create a file called 
/etc/modprobe.d/touchpad.conf

You can do this by typing 
sudo gedit /etc/modprobe.d/touchpad.conf
in your terminal (Applications --> Accessories --> Terminal).  It will ask for your password

when the file opens put in it
options psmouse proto=imps 
Save the file and restart.

Hope this works for you  :P

Works perfectly! Thanks a lot!! :popcorn:

This tip should really get pinned or something! :)

---

### Post by timur_ba on 2010-06-07
Check [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727)
I don't know when, was it updates or some changes, but mine touchpad also stopped working.

---

### Post by Spac3man on 2010-07-08
Hello.
After applying that fix, edge scrolling no longer works, and mouse options no longer offer touchpad options!

---

### Post by kamlendu on 2010-08-27
> **Hopper122 said:**
> Found a fix that worked for me.  I am using a HP Pavilion dv9000 touch pad stopped working but a USB mouse would work fine.  Also my touch pad would work in KDE but not in Gnome...  So either install KDE and use it or...

Create a file called 
/etc/modprobe.d/touchpad.conf

You can do this by typing 
sudo gedit /etc/modprobe.d/touchpad.conf
in your terminal (Applications --> Accessories --> Terminal).  It will ask for your password

when the file opens put in it
options psmouse proto=imps 
Save the file and restart.

Hope this works for you  :P


Yeh, It worked. You saved my day. Thanx. 
Some time my keyboard and touchpad freeze just on its own. In that case I need to restart the machine. It is frustrating, Any hopes?

---

### Post by linuxkid3 on 2010-09-19
The is now this page:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
and just installing the package gpointing-device-settings and rebooting worked for me.
don't know it is any help...:)
System/Preferences/Pointing devices
 to configure all the scrolling you want

---

### Post by mas_sergio on 2010-10-29
i have no idea what is going on either????????? first right click went out then when i put my computer to sleep and woke it up the mouse didn't work anymore. Could this be due to a new update? I also only have 1GB in my ubuntu partition and I was doing some heavy web browsing at the time watching many flash videos and such so I'm not sure if it's related to space or something that got messed up when I put it to sleep. i held the power button down and restarted several times and the mouse no longer WORKS! The only time the mouse seems to work is at login at the username selection menu after I type my pass the mouse goes from black(DMZ) to the white (its always done this no problems) and no longer works. I have a synaptic touchpad HP DV6700 Entertainment PC.


I just want to add:
I've worked so hard to customize my ubuntu install and put so many nice icons and themes and custom gnome menu's on it that it would be a shame to have to swipe ubuntu 10.04 off of my system and then to reinstall it all over again becuase of an issue with the mouse. W/o a mouse a computer is pretty much a brick. I have no idea how to use keyboard shortcuts. For now all I know is CTRL ALT DELETE brings up restart menu.  What is up with this issue/bug?
:confused::confused::confused::confused:

---

### Post by p1ggybank on 2010-12-03
I don't know anything about making the package, I followed the instructions to the t... it opened a blank note, and there is no option to put anything anywhere. I am so frustrated I almost want to go back to windows

---

### Post by hodged02 on 2011-02-13
> **Hopper122 said:**
> Found a fix that worked for me.  I am using a HP Pavilion dv9000 touch pad stopped working but a USB mouse would work fine.  Also my touch pad would work in KDE but not in Gnome...  So either install KDE and use it or...

Create a file called 
/etc/modprobe.d/touchpad.conf

You can do this by typing 
sudo gedit /etc/modprobe.d/touchpad.conf
in your terminal (Applications --> Accessories --> Terminal).  It will ask for your password

when the file opens put in it
options psmouse proto=imps 
Save the file and restart.

Hope this works for you  :P

this was a nice quick fix, for my acer 5335 thanks!!!

---

### Post by Curios on 2011-03-29
> **Hopper122 said:**
> Found a fix that worked for me.  I am using a HP Pavilion dv9000 touch pad stopped working but a USB mouse would work fine.  Also my touch pad would work in KDE but not in Gnome...  So either install KDE and use it or...

Create a file called 
/etc/modprobe.d/touchpad.conf

You can do this by typing 
sudo gedit /etc/modprobe.d/touchpad.conf
in your terminal (Applications --> Accessories --> Terminal).  It will ask for your password

when the file opens put in it
options psmouse proto=imps 
Save the file and restart.

Hope this works for you  :P

Works on a Dell Inspiron 11z!

I previously tried: 

synaptics-dkms
synclient Touchpad=0

Neither worked, but the above did the trick.

---

### Post by cruising on 2011-05-25
> **linuxkid3 said:**
> The is now this page:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
and just installing the package gpointing-device-settings and rebooting worked for me.
don't know it is any help...:)
System/Preferences/Pointing devices
 to configure all the scrolling you want

A beautiful fix! Simply awesome! Thanks for the post, linuxkid3!:guitar::)=D>

---

### Post by Clinic on 2011-10-26
> **Hopper122 said:**
> Found a fix that worked for me. I am using a HP Pavilion dv9000 touch pad stopped working but a USB mouse would work fine. Also my touch pad would work in KDE but not in Gnome... So either install KDE and use it or...
 
Create a file called 
/etc/modprobe.d/touchpad.conf
 
You can do this by typing 
sudo gedit /etc/modprobe.d/touchpad.conf
in your terminal (Applications --> Accessories --> Terminal). It will ask for your password
 
when the file opens put in it
options psmouse proto=imps 
Save the file and restart.
 
Hope this works for you 
 
Thanks, worked first go on my HP dv6000 under 11.10

---

### Post by mogorvabb on 2012-01-22
> **Hopper122 said:**
> Found a fix that worked for me.  I am using a HP Pavilion dv9000 touch pad stopped working but a USB mouse would work fine.  Also my touch pad would work in KDE but not in Gnome...  So either install KDE and use it or...

Create a file called 
/etc/modprobe.d/touchpad.conf

You can do this by typing 
sudo gedit /etc/modprobe.d/touchpad.conf
in your terminal (Applications --> Accessories --> Terminal).  It will ask for your password

when the file opens put in it
options psmouse proto=imps 
Save the file and restart.

Hope this works for you  :P

THX! works fine Hp Probook4520s

---

