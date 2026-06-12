---
title: "using python gnome applet in Unity"
date: 2011-05-11
forum: General Help
---

### Post by gamblor01 on 2011-05-11
I recently upgraded to 11.04 and I'm wondering how to get a Python applet I wrote to show up in the bar at the top (which no longer uses gnome-panel -- I'm not sure what it uses).  Previously I could just click on the bar and add whatever I wanted (just had to put the file in /usr/lib/bonobo/servers for it to show up in the list).  Now I can no longer do that.

I have also looked at creating a .desktop file with several menus options and placing it into my launcher but that doesn't work well, because the child processes seem to terminate and return immediately.  Specifically, I'm using this to stop/start Tomcat.  If the process terminates then it does me no good because it starts Tomcat, and as soon as the catalina.sh is done starting up, the process immediately terminates and it shuts down.  Thus, it isn't very useful for me to start Tomcat.

Previously I wrote a Python applet to control Tomcat.  If I can just figure out how to get that back into the top bar that would be great.  If anyone knows how to get something in the launcher to work (i.e. not kill the child process as soon as it is spawned and "finished") that would probably be even cooler!

---

### Post by kostkon on 2011-05-11
I think the best solution would be to convert your gnome panel applet to an application indicator (appindicator).

[There are already many appindicators]("http://askubuntu.com/questions/30334/list-of-application-indicators") that aren't just tray icons but have some extra functionality that you would find in a panel applet, e.g. the System Load Indicator.

Some documentation with code samples, [here]("https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators").

Hope that helps.

---

### Post by gamblor01 on 2011-05-12
Wow...that's a lot of reading to do.  I see some C and Python examples near the end though.  Maybe I can tweak one of those to work.

---

### Post by gamblor01 on 2011-05-13
Ok this is pretty sweet -- I just found a much simpler way to do this following this page as an example:

[http://askubuntu.com/questions/34597/how-do-i-make-a-custom-launcher-for-terminal-applications](http://askubuntu.com/questions/34597/how-do-i-make-a-custom-launcher-for-terminal-applications)


I wasn't too picky about making this fancy or general...I just need it to work, so paths are hardcoded and such.  Here is my .desktop file (which I put into ~/.local/share/applications):

```
[Desktop Entry]
Version=1.0
Name=Tomcat Manager
Comment=Start and stop Tomcat
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=/home/bdmayes/Pictures/custom-icons/tomcat-applet.png
StartupNotify=true
StartupWMClass=TomcatServer
X-Ayatana-Desktop-Shortcuts=Server1;Server2;Server3;

[Server1 Shortcut Group]
Name=Start Tomcat
Exec=tomcatStart.py
TargetEnvironment=Unity

[Server2 Shortcut Group]
Name=Stop Tomcat
Exec=tomcatStop.py
TargetEnvironment=Unity

[Server3 Shortcut Group]
Name=Restart Tomcat
Exec=tomcatReStart.py
TargetEnvironment=Unity
```


Then what I did was to create super simple Python scripts and put them in a directory that resides in my PATH:


```
$ cat tomcatStart.py 
#!/usr/bin/env python

import subprocess

subprocess.Popen("/home/bdmayes/Programs/apache-tomcat-6.0.32/bin/debug.sh");



$ cat tomcatStop.py 
#!/usr/bin/env python

import subprocess

subprocess.Popen("/home/bdmayes/Programs/apache-tomcat-6.0.32/bin/shutdown.sh");



$ cat tomcatRestart.py 
#!/usr/bin/env python

import subprocess

subprocess.Popen("/home/bdmayes/Programs/apache-tomcat-6.0.32/bin/restart.sh");
```


The shutdown.sh script is provided by Tomcat, but I have manually created debug.sh (to allow remote debugger connections on port 8000 so I can step through code) and restart.sh (to first run shutdown.sh, and then when the pid is gone, it fires up debug.sh again).

With everything in place I just dragged the .desktop file to my launcher and VIOLA!  Right-click the Tomcat icon and it works.  See attached picture for example.  :D

---

