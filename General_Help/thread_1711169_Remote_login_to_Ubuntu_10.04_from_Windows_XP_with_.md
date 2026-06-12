---
title: "Remote login to Ubuntu 10.04 from Windows XP with XDMCP"
date: 2011-03-20
forum: General Help
---

### Post by davidc3402 on 2011-03-20
I have to say that using XDMCP with Ubuntu 10.04 and Windows XP is exactly what I was looking for to remote in without a monitor. Thanks for those who posted to this thread [http://ubuntuforums.org/showthread.php?t=16953](http://ubuntuforums.org/showthread.php?t=16953). Even though it isn't installed initially for 10.04 it is possible to set this up. I hope this saves others time in their search and if I left out anything please let others know. I tried several things including Remote Desktop so I might of just in overtly left out something.
 
Since the original post I have also upgraded to 10.10 and it everything still seems to be working fine.
 
install XDM on the Ubuntu machine making it the default login screen.
install Xming on the windows machine
 
Edit /etc/X11/xdm/xdm-config and change this line: 
DisplayManager.requestPort: 0
and comment it out with an exclamation mark as: 
! DisplayManager.requestPort: 0
 
Edit /etc/X11/xdm/Xaccess by uncommenting this line:
#* # any host can get a login window
to: 
* # any host can get a login window
 
open 177 on windows firewall
open 6000 udp on the router and forward it to the Ubuntu ip
 
reboot Ubuntu
 
setup the xlaunch settings for windows:
-one window with Display 0
-Open session via XDMCP
-Connect to host and enter the ip of the Ubuntu machine
-Clipboard checked and additional parameters of -screen 0 1024 768
-Save configuration
It will then save a config file to the desktop then right click on it and use "open with", choose program, select Xlaunch and check always remember. I also renamed my config file to Ubuntu in case I add others later. Just double click it now and you should see a generic X window then a few seconds later a logon screen. If you had gnome set for your user account before after logon it will open up the gnome desktop automatically even though the logon is a generic logon screen. 
 
After you have gotten to your desktop go to the System menu-> then preferences->keyboard shortcuts to open the app for mapping keys. Find the one that says "Hide all normal windows and set focus to the desktop" and change the "D" to "Alt+d" by pressing the keys when the selection is highlighted in the window. This is needed because if you don't when you are in any window during a session and you type the "d" character for anything it will minimize all the windows. The setting above will prevent that from happening.
 
I also blocked all outside IPs at the router since I am using this for personal use,
however others may want to review previous posts about using SSH for encryption also.

---

