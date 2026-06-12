---
title: "Command echo from terminal evoked by a script"
date: 2009-07-30
forum: General Help
---

### Post by willemto on 2009-07-30
Hi, I am not sure where to post this, but here is what I would be grateful to find any help.

I have a script:

#!/bin/sh
gnome-terminal --command "sh  -c  'echo Setting up VNC Server';'vncserver -geometry 1280x970 -depth 24'"

The script works, however the feedback I get is only from "echo Setting up VNC Server" and no feedback from vncserver part of the commands.

Evoking "vncserver -geometry 1280x970 -depth 24" directly from a terminal, shows:

New 'linuxbox:13 (willem)' desktop is linuxbox:13

Starting applications specified in /home/willem/.vnc/xstartup
Log file is /home/willem/.vnc/linuxbox:13.log

I would like to see this message in the created terminal, as well as the echo.

Any ideas?

---

### Post by sisco311 on 2009-07-30
Hi and welcome to the forums!

Try to redirect stderr to stdout:
```
#!/bin/sh
gnome-terminal --command "sh -c 'echo Setting up VNC Server';'vncserver -geometry 1280x970 -depth 24 **2>&1**'"
```

---

### Post by willemto on 2009-07-30
Fantastic. Thanks! I only had to add sleep, and now it works perfectly.

#!/bin/sh
gnome-terminal --command "sh  -c  'echo Setting up VNC Server';'vncserver -geometry 1280x970 -depth 24 2>&1 && sleep 20'"

---

