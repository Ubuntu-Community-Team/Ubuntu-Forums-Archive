---
title: "Run Transmission remotly"
date: 2011-08-10
forum: General Help
---

### Post by JCM_Pico on 2011-08-10
Hi there,

Hi have a computer working 24/7, although a reboot procedure was performed and now I've no way to get transmission running, since I have no physical access to the machine.
The only way I can access is throw ssh.

Does any one knows any way of get it started?

---

### Post by 3Miro on 2011-08-10
You may run transmission as a daemon and manage it remotely:

[http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html](http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html)

---

### Post by JCM_Pico on 2011-08-10
Has I understand, the link that you have posted explain a way to control transmission remotely. Is it possible to just start it and let him running on the machine?

---

### Post by CatKiller on 2011-08-10
You might want to look into *screen*. Very useful for running things through SSH. There are many console-based BitTorrent clients available.

---

### Post by nothingspecial on 2011-08-10
If you have the .torrent files, in the same directory...

then ```
sudo apt-get install transmission-cli
```

Then
```

transmission-cli -g ~/.config/transmission *.torrent
```

If not there are other ways around it but slightly more complicated.

But as CatKiller says, look at screen so you can detatch the session.

---

### Post by doas777 on 2011-08-10
> **JCM_Pico said:**
> Has I understand, the link that you have posted explain a way to control transmission remotely. Is it possible to just start it and let him running on the machine?
please read closer, as the instructions you seek are there.

installing transmission as a daemon will cause it to run automatically on startup, without any logged in user. Look carefully at the section on installing and configing transmission-daemon.

once you have gotten it installed configed and running as a daemon, then you can control it remotly via the web interface as you noticed.

---

### Post by JCM_Pico on 2011-08-10
the .torrent files are configure to be added automaticly. I just want to start the program and let him running  :D

---

### Post by JCM_Pico on 2011-08-10
thanks all of you problem solve, installing the daemon...

---

