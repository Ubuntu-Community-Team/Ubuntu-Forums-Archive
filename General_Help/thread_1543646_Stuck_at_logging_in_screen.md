---
title: "Stuck at logging in screen"
date: 2010-08-01
forum: General Help
---

### Post by plzdontkillme11 on 2010-08-01
I'll start from the beginning. This is going to be kinda long, so bear with me.

When I clicked on the "networks" icon the "enable wireless" button was greyed over (I couldn't click on it). So I restarted for a quick fix.

Now the problems started.

Restart was very slow and choppy. When it finished, it opened up a login  screen, which was weird since I had the automatic login enabled. I put  in my password ad logged in... the screen flashed, and I came right back  to the login screen. I did this about three times with the same  results.

I restarted with the terminal (alt-F2). A message popped up saying that I  was in low-graphics mode. I clicked ok. Now, I don't have a "quiet"  splash screen. The system tells me what's being loaded and whatnot. For  this restart, the screen didn't move. It stopped at "Checking battery  state," or I think that's what it's called.

The second restart, it stopped at "loading vignesh" (my profile). I  restarted agian and set graphics back to default. Of course, I'm once  again stuck at m login screen.

Disk checks in the live CD came clean. I removed any broken packages and reinstalled them with the terminal. I reinstalled the ubuntu-desktop just for kicks (sudo apt-get install ubuntu-desktop).

This may not be relevant, but the "enable wireless" under "Networks" was grayed over as well in the Live CD (I couldn't click on it at all). 

This a repost (with edits, of course). Thanks to the mod for setting me straight. I'm not good at technical issues like this so you have to tell me what other information I have to give.

Thanks in advance.

EDIT:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1469070](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1469070)

This is almost exactly what's happening to me. I would try the solution, but I don't know how to access the grub boot menu.

---

### Post by plzdontkillme11 on 2010-08-01
Not sure if this was clear, but I can login to the terminal.

---

### Post by dino99 on 2010-08-01
its time to look at usefull errors logged into:

- .xsession-errors (/home, ctrl+h to unhide)
- system admin logviewer

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

---

### Post by plzdontkillme11 on 2010-08-01
Thanks for the reply. I can't access those files because I can't login. I am in the terminal I accessed from the Login screen with ctrl-alt-F2. One minute, let me try the other commands in your post.

---

### Post by plzdontkillme11 on 2010-08-01
sudo apt-get install -f : nothing happened.

sudo dpkg --configure -a: nothing happened.

sudo dpkg-reconfigure jockey: jockey not installed.

sudo dpkg-reconfigure gdm: nothing happened.

sudo dpkg-reconfigure plymouth: "update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic"

---

### Post by plzdontkillme11 on 2010-08-01
YES! I fixed it!

I removed gdm and installed kdm. Everything's working fine now. 

Thanks.

---

