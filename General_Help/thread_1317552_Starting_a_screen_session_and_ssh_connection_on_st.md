---
title: "Starting a screen session and ssh connection on startup"
date: 2009-11-06
forum: General Help
---

### Post by Bobly on 2009-11-06
[color=red][b]This question has been reposted with a more accurate title, however I am unable to delete this post, if you're looking for the solution to a similar problem consider reading the new question on this post: http://ubuntuforums.org/showthread.php?p=8264346

If a mod drops by, this can now be deleted unless anyone responds with an answer.[/b][/color]

> Hey Guys,

I'm having a bit of issues setting up a script that will automatically set up an SSH Tunnel with a forwarded port to a remote server in a screen session on boot.


The goal: Set up a SOCKS5 proxy via SSH Tunneling which sets itself up automatically.

How I'm trying to achieve this: Launch a screen session in daemon mode with autossh setting up the tunnel (screen -dmS tunnel autossh -M 0 -o "ServerAliveInterval 60" -o "ServerAliveCountMax 3" -D 8080 xxx.xxx.xxx.xxx)


I'm having a hard time finding accurate information in how to achieve this, but while I was first trying to use /etc/init.d/rc.local, from what I understand Debian doesn't use rc.local, before then trying creating a script in /etc/init.d and using update-rc.d, but it looks like those are executed before logging in, so I'm now trying to create a script which is launched by "Startup Applications" (gnome-session-properties).



Setup: Ubuntu Karmic Koala on an Asus EEE 901, changed very little since I did a clean install of Karmic (which btw runs much better than Jaunty on 901, everything seems to work natively and it's MUCH faster, even compiz works).

I've got a "autosshtunnel" file in ~/Scripts/, which I've set to chmod u+x ( [http://ubuntuforums.org/showthread.php?t=1216683&highlight=startup](http://ubuntuforums.org/showthread.php?t=1216683&highlight=startup) ) and set to launch in Startup Applications but I can't think of what I'm doing wrong...

I've tried the three following ways of writing the script to be executed:

```
screen -dmS tunnel autossh -M 0 -o "ServerAliveInterval 60" -o "ServerAliveCountMax 3" -D 8080 xxx.xxx.xxx.xxx
```

```
#!/bin/sh
screen -dmS tunnel autossh -M 0 -o "ServerAliveInterval 60" -o "ServerAliveCountMax 3" -D 8080 xxx.xxx.xxx.xxx
```

```
#!/bin/bash
screen -dmS tunnel autossh -M 0 -o "ServerAliveInterval 60" -o "ServerAliveCountMax 3" -D 8080 xxx.xxx.xxx.xxx
```

Everytime I reboot, there is no screen session running or tunnel set up, any ideas?

PS: If it's possible I'd rather use screen + autossh as I can keep an eye on it and use the shell session for other stuff if need be at times however I am open to other suggestions.



Edit: The script has been tested manually and works fine, I just can't get it to run automatically.

---

