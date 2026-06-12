---
title: "Auto logoff command when Startup App is Terminated"
date: 2010-12-17
forum: General Help
---

### Post by sheehanw on 2010-12-17
I am using Ubuntu as the client machine operating system. I have a start up program to connect to a Windows terminal Server. I am needing assistance in how I can force the client to logoff if the terminal connection is terminated for any reason. This is more of a security issue as we do not want the students using the computer to access the loacl machine at all. The program works great on boot, but it shows the home screen when terminated. 
 
Thanks,

---

### Post by Brandon Williams on 2010-12-17
Instead of running the remote desktop app as a startup application within a standard session login, you can use a custom session that runs the terminal services client as its only app. You would run it in fullscreen mode and you would not run it within a "real" window manager session.

First, create an executable script that launches the terminal services client; a possible name would be /usr/local/bin/start_tsclient.sh, which would look something like this:```
#!/bin/sh
exec command
```with "command" being the command line that you currently run as your startup application within the standard login session. This file would be created using sudo, and then you would change the permissions with "sudo chmod 755 /usr/local/bin/start_tsclient.sh".

Next, create a .desktop file to describe the session type for gdm. You can use /usr/share/xsessions/xterm.desktop as a guide. Your file could be called /usr/share/xsessions/tsclient.desktop, and it might look something like this:```
[Desktop Entry]
Encoding=UTF-8
Name=tsclient
Comment=Terminal services client.
Exec=/usr/local/bin/start_tsclient.sh
TryExec=/usr/local/bin/start_tsclient.sh
Icon=
Type=Application
``` Once again, create the file using sudo, and then change the permissions with "sudo chmod 644 /usr/share/xsessions/tsclient.desktop".

I think that this should be enough to add a new session to the gdm login screen that will start a terminal services client as the only running application in the session and then exit the session when the terminal services client is closed.

---

