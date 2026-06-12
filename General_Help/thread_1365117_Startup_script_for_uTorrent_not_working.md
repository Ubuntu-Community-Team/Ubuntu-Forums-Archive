---
title: "Startup script for uTorrent not working"
date: 2009-12-26
forum: General Help
---

### Post by amphibem on 2009-12-26
I am looking for some help getting uTorrent to automatically start in 8.04. I have done some googling and put some stuff together but no go quite yet. And before someone suggests I use another client, I need something with a webui, scheduler and is usable by non-technical users who are familiar with uTorrent. Hence I think uTorrent under WINE is my best best. So far I have
1. Got uTorrent w/ webui working through WINE
2. Created the below script to run uTorrent. This works fine when run manually.

```
#!/bin/bash
wine '/home/mc/.wine/drive_c/Program Files/uTorrent/uTorrent.exe' >/dev/null 2>&1
```

3. Called the script start-utorrent.sh and placed in /etc/init.d
4. Ran command 
```
sudo update-rc.d start-utorrent.sh defaults 
```
to make the script run at startup, this ran and reported success.


However when the computer boots uTorrent is not loaded, and does not show up under top. 
Is this simply not a process that will work for a GUI program like uTorrent? Is there something that will work? This machine will be headless so I need uTorrent to start whenever it is re-started.

---

### Post by switch10 on 2009-12-26
you should try Deluge.  It is a utorrent clone and it works exactly like it..  It is the best clone I have ever seen.

```
sudo apt-get install deluge
```

---

### Post by lovinglinux on 2009-12-26
Deluge is the way to go. See [http://ubuntuforums.org/showthread.php?t=1114965](http://ubuntuforums.org/showthread.php?t=1114965)

With deluge you can also connect via remote GTK interface, which means it looks like you are downloading from your own computer, but in fact you are connected to the headless server. It's way much better than web ui.

---

### Post by amphibem on 2009-12-26
Thanks very much **switch10**, although I still don't have the auto-start feature I want although I assume this will be easier with a native program.

There are some basic instructions [here]("http://www.linuxscrew.com/2007/08/09/autostart-programs-in-ubuntu/") but because this is Mythbuntu I don't have 'Preferences' or 'Sessions'. Is there an cli equivalent to the linked instructions, or can I add that control panel to my install without upgrading to a complete Ubuntu desktop?

Edit:
Seen **lovinglinux**'s post, off following the linked instructions now.

---

### Post by amphibem on 2009-12-26
OK followed the instructions on lovinglinux's link and got an insal of Deluge that just locks up when started. So I gave up and went back to 0.5, but I still can't make Deluge load at boot. In this case the scripts don't seem to work when run manually, I can't connect to the webui. 

A couple of other related questions;
1. For 'username' is that the "Name" or the "Login name"?
2. Can someone point me to info on this GTK interface, not something I am familiar with

Edit: Finally got everything working, running Deluge 1.2 with a headless server-client setup, with the daemon auto-loading. Thanks to all for your help

---

