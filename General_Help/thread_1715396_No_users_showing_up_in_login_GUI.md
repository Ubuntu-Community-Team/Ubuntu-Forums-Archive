---
title: "No users showing up in login GUI"
date: 2011-03-26
forum: General Help
---

### Post by Egat on 2011-03-26
I no longer see any users in the login screen GUI for Ubuntu.

Installed fresh Ubuntu 10.10 to dual boot with Win7 this morning. Got everything working, and promptly forgot my password. So I followed the method #1 directions to reset my password here:
[http://www.botskool.com/geeks/how-recover-your-ubuntu-1004-password](http://www.botskool.com/geeks/how-recover-your-ubuntu-1004-password)

On restart I was able to login just fine.

I'd like to use the laptop to download MP3's from Amazon during a DJ gig tomorrow, so I followed the directions to install libboost 1.34 in this thread:
[http://ubuntuforums.org/showthread.php?t=1478214](http://ubuntuforums.org/showthread.php?t=1478214)

Opened a terminal and pasted the commands from the thread into the terminal. On the "sudo dpkg -i *.deb" command I got an error. I don't have the exact error, but it was something about access to a database was denied because it was being used by another process. I decided to restart to see if that would free up the database resource, however upon restart I was greeted with an Ubuntu login screen now strangely devoid of selectable users.

I am able to login to the terminal (alt+ctrl+f2). I've tried going back to the recovery console to create a new user, but still nothing shows up in the login GUI. The login window appears, but no users are in the list. The computer name changes to "Ubuntu 10.10" and back when I click it. The Universal Access Preferences windows appear to work, however the restart/shutdown buttons do not function, I have to use the power button or "reboot -f" in the terminal to force the computer to reboot.

I'd love to avoid simply doing a clean re-install and use this as a learning experience. Any ideas?

---

### Post by linuxuser12345 on 2011-03-26
Click the "Other" button and manually type in the name and try to log in that way.
Does it work?

---

### Post by Egat on 2011-03-26
There is no other button either.

I've attached a picture of my login screen. Sorry for quality, it was taken from my phone as I can't figure out a way to take screenshots.

---

### Post by Krytarik on 2011-03-26
Did you already try re-installing "gdm"?:
```
sudo apt-get install --reinstall gdm
```

---

### Post by Egat on 2011-03-26
Reinstall of gdm and a reboot did the trick! Thanks!

---

