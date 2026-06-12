---
title: "Can't get past login screen"
date: 2009-11-25
forum: General Help
---

### Post by dogbert55 on 2009-11-25
When the computer starts up it gets to the login screen. It accepts my password, but then it just returns me to the same login screen.  I know my user name and password are correct because I can start a xterm session and login.  It just won't work for an xfce session.  I changed the nvidia-settings and installed a game right before it stopped working.  I tried uninstalling the game and changing the settings back, but to no avail. Any ideas?

---

### Post by jacobs444 on 2009-11-25
You can try: 
sudo dpkg-reconfigure xserver-xorg

---

### Post by akakingess on 2009-11-25
> **dogbert55 said:**
> When the computer starts up it gets to the login screen. It accepts my password, but then it just returns me to the same login screen.  I know my user name and password are correct because I can start a xterm session and login.  It just won't work for an xfce session.  I changed the nvidia-settings and installed a game right before it stopped working.  I tried uninstalling the game and changing the settings back, but to no avail. Any ideas?

I just went through the same thing and had to do a clean install (fortunately, I have a seperate /home partition) and everything came right back up. If you can, at least try to backup your home folder/s and then try a clean install, worst case I guess you could do it from the live CD if you have something to back them up to.

---

### Post by dogbert55 on 2009-11-25
I figured it out. When I tried startxfce4 from the command line, I got an error about not being able to access file /home/username/.ICEauthority. I deleted the file and was able to log in.  Thanks for the quick posts though.  I'm a few days from finals and was getting a little worried.

---

