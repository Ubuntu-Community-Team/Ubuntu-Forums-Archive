---
title: "No Ratings in Software Center"
date: 2011-05-16
forum: General Help
---

### Post by xjonquilx on 2011-05-16
For some reason when I reinstalled Ubuntu 11.04 Natty the ratings disappeared from the Software Center. How do I get them back?

---

### Post by Frogs Hair on 2011-05-16
Hi and Welcome

Try running the update manager an then check it. Another option is to locate the software in the Synaptic Package Manager , right click and mark for re- installation and select apply .

---

### Post by xjonquilx on 2011-05-16
I already tried all of that...

---

### Post by Frogs Hair on 2011-05-16
I don't know what the problem would be , I thought the package may not have installed correctly . Try starting via the terminal and see if there are errors that may give some clues .```
software-center
```

---

### Post by xjonquilx on 2011-05-16
```
jonquil@ubuntu:~$ software-center
2011-05-16 17:22:38,251 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/dbus/proxies.py', 400, '_introspect_error_handler')'
2011-05-16 17:22:38,250 - dbus.proxies - ERROR - Introspect error on :1.245:/org/gnome/zeitgeist/log/activity: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2011-05-16 17:22:38,277 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/backend/zeitgeist_simple.py', 40, '__init__')'
2011-05-16 17:22:38,276 - root - WARNING - can not get zeitgeist client: 'org.freedesktop.DBus.Error.ServiceUnknown: The name :1.245 was not provided by any .service files'
2011-05-16 17:22:39,359 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/view/widgets/mkit_themes.py', 675, 'retrieve')'
2011-05-16 17:22:39,358 - root - WARNING - No styling hints for Mac4Lin_GTK_Aqua_v1.0 were found... using Human hints.
/usr/share/software-center/softwarecenter/app.py:1192: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
2011-05-16 17:22:55,322 - softwarecenter.app - INFO - software-center-agent finished with status 1


```

---

### Post by Frogs Hair on 2011-05-16
I think it may have something  to with this error because when I run mine it says reconecting to zeitgeist engine. ```
2011-05-16 17:22:38,276 - root - WARNING - can not get zeitgeist client: 'org.freedesktop.DBus.Error.ServiceUnknown: The name :1.245 was not provided by any .service files'
```

I know nothing about the Mac 4 Lin theme , were you using that on the previous installation ?

---

### Post by xjonquilx on 2011-05-16
It's a theme that skins Ubuntu to look like Mac OS. Yes, I was using it on the last installation without any issues. However I can try switching themes and see if that alleviates the problem.

***later*** I tried switching themes but I'm still having the same issue. Maybe I should try reinstalling zeitgeist?

***later*** I tried reinstalling zeitgeist. Now I have ratings if I click specifically on something, but they don't show up in the main screen unless I click on the "more info" button for the program first and then go back to the main screen. This is getting stranger and stranger! Will post the output in terminal....

---

### Post by xjonquilx on 2011-05-16
```
jonquil@ubuntu:~$ software-center
2011-05-16 18:31:00,861 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/dbus/proxies.py', 400, '_introspect_error_handler')'
2011-05-16 18:31:00,860 - dbus.proxies - ERROR - Introspect error on :1.188:/org/gnome/zeitgeist/log/activity: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2011-05-16 18:31:00,880 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/backend/zeitgeist_simple.py', 40, '__init__')'
2011-05-16 18:31:00,880 - root - WARNING - can not get zeitgeist client: 'org.freedesktop.DBus.Error.ServiceUnknown: The name :1.188 was not provided by any .service files'
2011-05-16 18:31:01,177 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/view/widgets/mkit_themes.py', 675, 'retrieve')'
2011-05-16 18:31:01,176 - root - WARNING - No styling hints for Mac4Lin_GTK_Aqua_v1.0 were found... using Human hints.
/usr/share/software-center/softwarecenter/app.py:1192: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
2011-05-16 18:31:09,038 - softwarecenter.app - INFO - software-center-agent finished with status 1


```

---

### Post by Frogs Hair on 2011-05-16
I just saw this on another thread .```
zeitgeist-daemon --replace
```
It restarts the daemon.

---

### Post by xjonquilx on 2011-05-16
That didn't work either... still getting the same errors...

---

