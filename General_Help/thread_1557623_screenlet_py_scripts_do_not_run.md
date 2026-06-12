---
title: "screenlet py scripts do not run"
date: 2010-08-21
forum: General Help
---

### Post by histery on 2010-08-21
Hi,

I am a newbie to screenlets and ubuntu, but have some basic knowledge about linux. 

I was following the online instructions to install screenlets and all is fine and the manager appears as well.
In compiz the widget layer is active etc.
Once widget layer is activated it shows an empty blank dark screen, widgets are not running.
The widgets/scripts do not show up, neither on desktop nor on the widget layer.

Running the py script from terminal showing following output:

> user@ubuntu:/usr/share/screenlets/Clock$ ./ClockScreenlet.py 
CachingBackend: Loading instances from cache
Found a running session of Clock, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.Clock was not provided by any .service files
Screenlet has already been added to /tmp/screenlets/screenlets.owner.running
Loading instances in: /home/owner/.config/Screenlets/Clock/default/
No instance(s) found in session-path, creating new one.
Traceback (most recent call last):
  File "./ClockScreenlet.py", line 459, in <module>
    screenlets.session.create_session(ClockScreenlet)
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 472, in create_session
    session.start()
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 246, in start
    sl = self.screenlet(session=self, id=self.__get_next_id())
  File "./ClockScreenlet.py", line 125, in __init__
    **keyword_args)
  File "/usr/lib/pymodules/python2.6/screenlets/__init__.py", line 719, in __init__
    self.load_buttons(None)
  File "/usr/lib/pymodules/python2.6/screenlets/__init__.py", line 1099, in load_buttons
    self.closeb = self.gtk_icon_theme.load_icon ("gtk-close", 16, 0)
gio.Error: Error opening file: No such file or directory
> user@ubuntu:/usr/share/screenlets/ACPIBattery$ ./ACPIBatteryScreenlet.py 
CachingBackend: Loading instances from cache
Creating new entry for ACPIBatteryScreenlet in /tmp/screenlets/screenlets.owner.running
Loading instances in: /home/owner/.config/Screenlets/ACPIBattery/default/
No instance(s) found in session-path, creating new one.
Traceback (most recent call last):
  File "./ACPIBatteryScreenlet.py", line 302, in <module>
    screenlets.session.create_session(ACPIBatteryScreenlet)
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 472, in create_session
    session.start()
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 246, in start
    sl = self.screenlet(session=self, id=self.__get_next_id())
  File "./ACPIBatteryScreenlet.py", line 54, in __init__
    screenlets.Screenlet.__init__(self, uses_theme=True,width=100,height=50, **keyword_args)
  File "/usr/lib/pymodules/python2.6/screenlets/__init__.py", line 719, in __init__
    self.load_buttons(None)
  File "/usr/lib/pymodules/python2.6/screenlets/__init__.py", line 1099, in load_buttons
    self.closeb = self.gtk_icon_theme.load_icon ("gtk-close", 16, 0)
gio.Error: Error opening file: No such file or directory
what is the matter here, how to fix this?
thanks for any helpful advice.

---

### Post by histery on 2010-08-21
anybody, any idea?

.

---

### Post by histery on 2010-08-22
really? 
nobody has an idea?
Well, I still do have a fresh standard Ubuntu installation, with all updates installed, plus the screenlets enabled.

With the above error messages I don't know what to do, how to make them running?
Any permission missing, or what's wrong?
Please help, I am stuck here.

---

