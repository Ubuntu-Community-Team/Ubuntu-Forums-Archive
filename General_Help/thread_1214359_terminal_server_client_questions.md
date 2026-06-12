---
title: "terminal server client questions"
date: 2009-07-15
forum: General Help
---

### Post by davewave918 on 2009-07-15
ok my 1st post....hope this is the correct location for this sort of question

i use the terminal server client heavily as i have to support a windows environment from my ubuntu workstation

1. i have noticed the client will remember your password if you type it in the password field prior to connecting, is there a way to disable this feature?

2. after logging out from a session the client will attempt to reconnect over and over again until you hit cancel, is there a way to disable that also?

im using tsclient 0.150

anyway im sure there is some better way such as rdesktop with the correct commands but im just not that familiar with it yet and still getting used to the OS.

---

### Post by LepeKaname on 2009-07-15
rdesktop from command line is quite easy and once have the settings you want, you can create a simple add an alias to your .xinitrc (or create a bash file) to launch it.

This is one command I use:

```
rdesktop -g 1024x768 -u your_user SERVER.IP.ADDRESS
```

There are many options you can use (look at rdesktop --help). If you want to "autologin", then use:

... -u your_user -p your_password ...

One option I usually use, is "-a 8" which means only use 256 colors (which it will be faster). You can use also "-z -P" to increase performance. Use -f if you want full screen.

Using command line, you avoid the "problems" you described.

You can use VNC as well... Just install any VNC server in you windows computer and install x11vnc (the one I use, but there are some others) in Linux.

---

