---
title: "Can only log in from command line, not gui."
date: 2010-06-21
forum: General Help
---

### Post by Landercat on 2010-06-21
I apologize if this is not the correct area to post this, but I wasn't sure exactly which category this should go under.  

I have a HP/Compaq 6715b laptop and installed Ubuntu 10.04 about 3 days after it's release.  

Everything has been working fine, but when I tried to boot it up today it's not allowing me to log in from the gnome log-in screen.  I put in my username and password, the screen goes blank for a few seconds and it looks like everything is ok, then it brings up the log-in screen again.  I've tried logging in multiple times but it keeps coming back to the log-in screen.  

I did some searching through Google about this issue and couldn't find anything specific, but here's what I've tried so far.  

I rebooted and chose to go into recovery mode and chose the low graphics option.  This gave me the same results when trying to log-in normally.    

I rebooted again, went to recovery mode and chose drop to root shell prompt with networking.  From here I was able to log-in after typing the command "login". 

I ran apt-get update, then apt-get upgrade.  Rebooted again and tried to log-in like normal.  It kept coming back to the log-in screen again.  

I rebooted again and chose to go to recovery mode and then chose drop to root shell prompt.  

From here I tried /etc/init.d/gdm start
I received a message "WARNING: failed to acquire org.gnome.displaymanager"

Next I tried /etc/init.d/service gdm start
This gave me a message "Rejected send message"

I'm not sure what to try next, any help would be greatly appreciated.

---

### Post by Landercat on 2010-06-21
I got it working finally.  This may night be the "right" fix, but it was for me.  

I went back to the root shell prompt with network support and did the following.  

sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo dpkg-reconfigure xserver-xorg

I restarted and it seems to be working ok now.  If anyone else has any thoughts or suggestions on what happened or if there is a better fix I would be happy to read them.

---

