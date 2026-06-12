---
title: "Executing a script on startup"
date: 2009-11-07
forum: General Help
---

### Post by Bobly on 2009-11-07
Hey Guys,

I'm having a bit of issues setting up a script that will automatically set up an SSH Tunnel with a forwarded port to a remote server in a screen session on boot.


The goal: Set up a SOCKS5 proxy via SSH Tunneling which sets itself up automatically.

How I'm trying to achieve this: Launch a screen session in daemon mode with autossh setting up the tunnel (screen -dmS tunnel autossh -M 0 -o "ServerAliveInterval 60" -o "ServerAliveCountMax 3" -D 8080 xxx.xxx.xxx.xxx).


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



Edit Edit: In the Startup Applications menu, I've tried both just linking to the script file in the "command" box with the browse button as well as using "exec /home/user/Scripts/nameofscript", neither of which seem to be executing.

---

### Post by Barriehie on 2009-11-07
Similar request [here](http://ubuntuforums.org/showthread.php?t=1312689).  Hope that perhaps helps.

Barrie

---

### Post by Bobly on 2009-11-08
Thanks for your response barriehie but I don't think it's the answer to my problem.

From what I understand, that thread is about someone wanting to make a script that can set up something that auto start ups, however it's using the init.d method which runs before logging in, I'm looking to run a script after the user logs in, when the different applications run. As you'll see it's more of an application than a script just to configure something.

Any other ideas? I'm not getting anywhere on my own here :(



Edit: Tried adding my script to /usr/bin/, I can now run it simply by typing the name of the script in a terminal window, changed the startup applications menu to reflect this from the path to the script to simply the script name, and it still doesn't launch on reboot...

---

### Post by Bobly on 2009-11-08
Bump: Okay I still haven't managed anything, I tried buffing out the script, adding a bit that launched gnome-terminal first, and then a pause, but the problem with that is that a/ it takes longer, and b/ if the window doesn't keep focus the command doesn't get typed in the terminal window which basically means I'd have to wait until it's all done before being able to do anything which will be annoying if I'm in a hurry to start it up and start taking notes...

---

### Post by Barriehie on 2009-11-08
Never mind this one - See my next post!


> **Bobly said:**
> Bump: Okay I still haven't managed anything, I tried buffing out the script, adding a bit that launched gnome-terminal first, and then a pause, but the problem with that is that a/ it takes longer, and b/ if the window doesn't keep focus the command doesn't get typed in the terminal window which basically means I'd have to wait until it's all done before being able to do anything which will be annoying if I'm in a hurry to start it up and start taking notes...

What about invoking the terminal like this:
```

gnome-terminal --command=/Path2Script/MyScript.sh

```

Barrie

Edit: This should invoke the terminal and execute the command following --command=, alternatively -e <command to execute>.

---

### Post by Barriehie on 2009-11-08
Okay, I got my machine to run my ffclean.sh script when it started.  You can find autostarting programs in ~/.config/autostart/  These are plain jane .desktop files.  I think the names have to be all lowercase because mine didn't work with any caps in it.  All of the files have the blank line at the top so that may make a difference.  In my ffclean.sh script I have it echo a dummy file name to the desktop so I know that it ran.  I logged out and when presented with the login screen, wanting username, I F10 to select GNOME session instead of last and it worked.

I can't find it in the system monitor so I'm not sure how/if it ended! (I'm better with PHP than bash...:) ) 

The desktop entry specification can be found [here](http://standards.freedesktop.org/desktop-entry-spec/latest/index.html).

```


[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=No Name
Name[en_US]=MyTerminal
Exec=bash -c /home/barrie/bin/ffclean.sh
X-GNOME-Autostart-enabled=true
Comment[en_US]=TestStartUp
Comment=TestStartUp
GenericName=

```

---

### Post by Bobly on 2009-11-09
FINALLY I FOUND THE SOLUTION :D



Okay first of all let me explain in case people find this in the future and actually want to know what the solution is.

I tried different ways of writing the script, different ways of calling it, setting in timers, and nothing was working.

Eventually I noticed that the reason it wasn't working was because when starting up the computer isn't connected to the internet, so autossh exits and because screen is in daemon mode it exits too. A potential solution was to have a 60 seconds timer before launching it but whenever the internet dies it would all stop so here's how I've got it working:





/home/user/tunnelholder
```
#!/bin/bash
screen -dmS tunnel /home/bobly/Scripts/tunnelloop
```

/home/user/tunnelloop
```
#!/bin/bash
while [ 1 ] ; do autossh -M 0 -o "ServerAliveInterval 30" -o "ServerAliveCountMax 3" -D 8080 xxx.xxx.xxx.xxx ; echo "No internet connection, retrying in 30 seconds" ; sleep 30 ; done
```

Then just set /home/user/tunnelholder to run on startup in Startup Applications GUI.

It tries to establish a ssh + tunnel connection every 30 seconds, and once it's established it checks it every 30 seconds.

Solved :D

---

