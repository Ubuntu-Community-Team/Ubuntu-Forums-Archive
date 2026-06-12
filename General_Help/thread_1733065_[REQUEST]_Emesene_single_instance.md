---
title: "[REQUEST] Emesene single instance"
date: 2011-04-18
forum: General Help
---

### Post by D0nJ0seph on 2011-04-18
Hello people.
Well, in other post i asked if you know any way to just run emesene once. i found out that can be done with this command
[PHP]emesene -s[/PHP]but, it only stop emesene from opening. I want a script that prevents emesene to open twice, and if another instance is running then bring it to the front. Or open it from tray.

I found the same problem in skype but i found a script that is like this
[PHP]#!/usr/bin/env python
import dbus
import sys
import os

try:
    # Try and set skype window to normal
    remote_bus = dbus.SessionBus()
    out_connection = remote_bus.get_object('com.Skype.API', '/com/Skype')
    out_connection.Invoke('NAME mySkypeController')
    out_connection.Invoke('PROTOCOL 5')
    #out_connection.Invoke('SET WINDOWSTATE MAXIMIZED')
    out_connection.Invoke('SET WINDOWSTATE NORMAL')
    out_connection.Invoke('FOCUS')
except:
    os.system("skype")
    sys.exit()[/PHP]Just saved in *_/usr/local/bin/_* and that's all :D 
i'll attach the file with the command
Does anybody knows if there's something similar for emesene? THANKS

---

