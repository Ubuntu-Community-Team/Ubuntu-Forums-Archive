---
title: "Start program automatically on login."
date: 2006-06-16
forum: General Help
---

### Post by acolic on 2006-06-16
Hi,

I'm using Blackbox. Is there a way to start a program automatically on login?

I'd like to start conky every time I log into my computer.

Thanks

Alex

---

### Post by ayoli on 2006-06-16
maybe that can help:
[http://blackboxwm.sourceforge.net/BlackboxFAQ/StartupAndShutdown]("http://blackboxwm.sourceforge.net/BlackboxFAQ/StartupAndShutdown")

---

### Post by bluevoodoo1 on 2006-06-16
Yes it is possible. Depends on your comfort level with creating and editing files. Assuming you are comfortable, here we go. 

1. We make a startup script.
2. We change the path of exec blackbox in /usr/share/xsessions/blackbox.desktop

1. We create a script.
```
gedit ~/.bbstartup.sh
```
and paste this in
```

#!/bin/sh

conky &
exec /usr/local/bin/blackbox

```
then make it executable
```
chmod +x ~/.bbstartup.sh
```

2. We change the path of exec blackbox in /usr/share/xsessions/blackbox.desktop

first a backup.
```
sudo cp /usr/share/xsessions/blackbox.desktop /usr/share/xsessions/blackbox.desktop_backup
```
then
```
sudo gedit /usr/share/xsessions/blackbox.desktop
```

Before we change anything, It will look something like this...
```

[Desktop Entry]
Encoding=UTF-8
Name=BlackBox
Comment=Highly configurable and low resource X11 Window manager
Exec=/usr/local/bin/blackbox
Terminal=False
TryExec=/usr/local/bin/blackbox
Type=Application
```

then we change the Exec and TryExec to the path of the newly created script. Replacing bluevoodoo1 with your username.
```

[Desktop Entry]
Encoding=UTF-8
Name=BlackBox
Comment=Highly configurable and low resource X11 Window manager
Exec=/home/**bluevoodoo1**/.bbstartup.sh
Terminal=False
TryExec=/home/**bluevoodoo1**/.bbstartup.sh
Type=Application
```

Logout, and hopefully you'll be all set.

---

