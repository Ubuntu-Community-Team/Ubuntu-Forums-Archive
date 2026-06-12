---
title: "Unable to log-on using the graphic interface"
date: 2010-02-14
forum: General Help
---

### Post by benbong on 2010-02-14
Hi All,

I have Ubuntu 9.10 x86_64.
I've installed Ubuntu in dual boot (my work still requires windows vista...).
It has work well for some time, and lately I saw a kernel update (2.6.32-17), and as I like to have the latest version of everything, I did it.
After the update, I've restarted to boot on my new kernel and when I reach the login screen, I enter my login and passowrd, and after some screen flickers, I'm back to the exact same screen.
I tried another password -> incorrect password detected.
I logged on on another TTY (no-X), and it works.

I've then read some threads in this forum and tried to reinit gdm, to delete all the nvidia drivers and boot with the xserver-xorg-core. but nothing works.

I don't want to end up re-installing ubuntu. 

If anyone has a clue, I'll be really thankful.

My Pc:
- core 2 quad Q9550
- 4 Gb RAM
- 1 * 500 Gb WD system hard drive (400 Gb Windows, 100 Gb Linux)
- 1 * 500 Gb WD + 1 * 250 Gb WD (Stock)
- 1 * Geforce GTX275 (I also ply games :)
- 1 * DVD Burner

I had the nvidia 185 drivers.

Thanks for your help.
Benbong

---

### Post by lijcam on 2010-02-15
You could try regenerating your xorg config[FONT=monospace].

[/FONT]```
sudo nvidia-xconfig --output-xconfig=/etc/X11/xorg.conf
```Please make sure you read the man page for nvidia-xconfig first I do have an nvidia card and do not know what to expect and or what other switches are required.

---

### Post by flippo on 2010-02-15
Theres a folder in you home directory .xsession-errors which will have a log of your login.  If you have a second user you can try logging in as that user to see if you have an issue with some of the user's gnome configurations that is causing it to crash.  The user's gnome preferences are stored in different folders in your home directory, if one of those is giving you troubles something like the .gconf .gnome or .gnome2 directory may have a bad config in it.  You can try moving those and seeing if you can then log in.  

Although I don't think xorg is your issue your xorg log is in /var/log/Xorg.0.log you can find xorg errors with

```
sudo cat /var/log/Xorg.0.log | grep \(EE\)
```

If you figure anything else out (for example by looking at .xsession-errors) please keep us updated.

---

### Post by karlabe on 2010-02-15
Hi, I have a similar problem.
I updated last week but since then I could not make things work successfully.
the last installed kernel is 2.6.31.20-generic.
I tried using recovery, from which I checked for broken packages, but none were found. I can successfully log in, with any one of my two accounts, but cannot manage to start X. When I tried I got the msg: "XSession: unable to start X Session, no /home/karlabe/.xsession no session managers no widows managers and no terminal emulators found. etc

Any help is appreciated

---

### Post by flippo on 2010-02-15
Hello karlabe,

Speaking for the community, we would be very happy to help you with your problem, but it is different from the one posted here.  benbong's X session starts, yours does not.  Please start a new thread for this problem.

---

