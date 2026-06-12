---
title: "Remote into a Windows machine from Ubuntu"
date: 2010-05-20
forum: General Help
---

### Post by DnDer on 2010-05-20
I found a page from 2005 on ubuntu forums' archive, but I was wondering what the 2010 standard is?

My parents live halfway across the country, and their computer is a shambles, despite being taken to the "repair guy" twice. I need to log in and clean it out remotely, since I won't be able to go out there anytime soon at all.

They're running XP Home, and I'm using Karmic, but will probably make the upgrade this weekend to Lucid.

---

### Post by bodhi.zazen on 2010-05-20
If they are going to install Ubuntu, have them back up their data and install Ubuntu, then use ssh.

The other option is to use VNC, just be aware of the potential security issues (use a very strong password). If they do not know how to open a port, google search reverse VNC.

[http://ubuntuforums.org/showthread.php?t=299489](http://ubuntuforums.org/showthread.php?t=299489)

---

### Post by DnDer on 2010-05-20
They have no plans to use ubuntu. I just need to clean up their XP install.

Thanks for the line on VNC. I will research that.

---

### Post by Peter09 on 2010-05-20
I believe gnome-rdp is in the repositories for connection to a windows machine.

---

### Post by dtfinch on 2010-05-20
I've used CrossLoop for remoting to non-technical users, since the setup on their end is minimal. It's just a wrapper around tightvnc that uses their server as a proxy, so you don't have to set up port forwarding. They just run it, which gives them an access code to give to you, which you enter on your end to connect. I haven't tried it on Linux yet, but it supposedly works on Wine.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6131](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6131)

edit: "Gold" rating threw me off. Looks like a real pain to install on Wine.

---

### Post by CharlesA on 2010-05-20
If it is XP Home, it doesn't have Remote Desktop on it, you would need to use VNC on it. 

Just assign a very strong password to VNC, and you should be ok.

If you don't want to do that, I've heard good things about Gotoassist express, but as far as I know it is only supported on PC/Mac, not Linux.

---

### Post by Peter09 on 2010-05-20
To support my friends I use x11vnc, but the twist is that I use it in the reverse connection mode.

They issue the command - through a launcher- 

```
x11vnc -connect <my ip address>
```

I issue the command (before them)

```
x11vnc -listen
```

I will then gain control of their screen. the benifits are

1. No changes to their router, no open ports for security breaches
2. The connection is only active if they click the launcher

I do need to open ports at my end but I am more security aware than they are.

---

### Post by CharlesA on 2010-05-20
That is only avalible on Linux, isn't it?

Nvm: [http://www.raymond.cc/blog/archives/2007/04/05/free-and-easy-remote-access-with-vnc-reverse-connections/](http://www.raymond.cc/blog/archives/2007/04/05/free-and-easy-remote-access-with-vnc-reverse-connections/)

---

### Post by Peter09 on 2010-05-20
I believe X11vnc is available for windows.

EDIT: Having said that I not so sure it is available :-(

---

### Post by drdos2006 on 2010-05-20
Have a look at TeamViewer. It has linux and windows programs.
regards
[edit]
Has Voip, FTP, chat etc...
Please post back here with your experience..
[/edit]

---

### Post by drdos2006 on 2010-05-20
As an Addendum, I also found NeoRouter for remote assistance. It also has a Ubuntu server and Windows client operation.
The difference I found between NeoRouter and teamViewer, was that the client could not see what the remote operator was dooing but the client could see what the remote operator was doing in TeamViewer.

NeoRouter may be more suitable for a slower connection than TeamViewer, but I have not tested them against each other over Internet connections, just used VM for testing.
Any other comments by any body else would be appreciated.

regards

---

