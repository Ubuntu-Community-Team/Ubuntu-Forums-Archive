---
title: "Screenlets Won't Launch"
date: 2010-10-15
forum: General Help
---

### Post by drmichael on 2010-10-15
I'm new to Ubuntu (just installed 10.10 yesterday) and I've been trying everything that I can to get screenlets to work.  The screenlets-manager starts up just fine and I can see the daemon running in the task bar, but when I try to launch ANY of the screenlets (clicking "Launch/Add" or checking "Start/Stop"), the Screenlets Manager window will go inactive, as though it tried to load the screenlet, but I can't see the screenlet at all.

Here is my terminal print-out:
```
username@M:~$ screenlets-manager

** (screenlets-manager.py:7066): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (screenlets-manager.py:7066): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (screenlets-manager.py:7066): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
/usr/share/screenlets-manager/screenlets-manager.py:93: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips = gtk.Tooltips()
/usr/share/screenlets-manager/screenlets-manager.py:414: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but1, _('Launch/add a new instance of the selected Screenlet ...'))
/usr/share/screenlets-manager/screenlets-manager.py:415: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but2, _('Install a new Screenlet, SuperKaramba or Web Widget or Web Application  ...'))
/usr/share/screenlets-manager/screenlets-manager.py:416: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but3, _('Permanently uninstall/delete the currently selected Screenlet ...'))
/usr/share/screenlets-manager/screenlets-manager.py:417: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but4, _('Reset this Screenlet configuration (will only work if screenlet isnt running)'))
/usr/share/screenlets-manager/screenlets-manager.py:418: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but5, _('Install new theme for this screenlet'))
/usr/share/screenlets-manager/screenlets-manager.py:419: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but6, _('Restart all screenlets that have auto start at login'))
/usr/share/screenlets-manager/screenlets-manager.py:420: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but7, _('Close all Screenlets running'))
/usr/share/screenlets-manager/screenlets-manager.py:421: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but8, _('New Screenlets Options/Properties'))
/usr/share/screenlets-manager/screenlets-manager.py:422: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but9, _('Create a Desktop shortcut for this Screenlet'))
/usr/share/screenlets-manager/screenlets-manager.py:477: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_about, _('Show info about this dialog ...'))
/usr/share/screenlets-manager/screenlets-manager.py:478: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_download, _('Download more screenlets ...'))
/usr/share/screenlets-manager/screenlets-manager.py:479: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_close, _('Close this dialog ...'))
File /home/username/.screenlets/config.ini not found
Starter already exists.
DAEMON FOUND!
True
Launch ClearCalendar
Launching Screenlet from: /usr/share/screenlets/ClearCalendar/ClearCalendarScreenlet.py
Logging output goes to: $HOME/.config/Screenlets/ClearCalendarScreenlet.log
REGISTER screenlet: ClearCalendarScreenlet
True
/usr/share/screenlets/ClearCalendar/ClearCalendarScreenlet.py:345: DeprecationWarning: use copy pango.FontDescription.set_family instead
  p_fdesc.set_family_static("Tahoma")
/usr/share/screenlets/ClearCalendar/ClearCalendarScreenlet.py:382: DeprecationWarning: use copy pango.FontDescription.set_family instead
  p_fdesc.set_family_static("FreeSans")
True
Launch DigiClock
Launching Screenlet from: /usr/share/screenlets/DigiClock/DigiClockScreenlet.py
Logging output goes to: $HOME/.config/Screenlets/DigiClockScreenlet.log
REGISTER screenlet: DigiClockScreenlet
True
/usr/lib/pymodules/python2.6/screenlets/drawing.py:114: DeprecationWarning: use copy pango.FontDescription.set_family instead
  self.p_fdesc.set_family_static(font)
True
True
True
Launch CopyStack
Launching Screenlet from: /usr/share/screenlets/CopyStack/CopyStackScreenlet.py
Logging output goes to: $HOME/.config/Screenlets/CopyStackScreenlet.log
REGISTER screenlet: CopyStackScreenlet
True
```

Here is my CopyStackScreenlet.log:
```
CachingBackend: Loading instances from cache
Found a running session of CopyStack, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.CopyStack was not provided by any .service files
Screenlet has already been added to /tmp/screenlets/screenlets.username.running
Loading instances in: /home/username/.config/Screenlets/CopyStack/default/
No instance(s) found in session-path, creating new one.
/home/username/.config/Screenlets/CopyStack/default/CopyStack1
[]
LOAD NEW THEME: default
FOUND: /usr/share/screenlets/CopyStack/themes/default
theme.conf found! Loading option-overrides.
theme.conf loaded: 
Name: Bars
Author: RYX (aka Rico Pfaus)
Version: 1.0
Info: A simple theme for the copystack.
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
Screenlet has been initialized.
[<__main__.UrlElement object at 0x2407c50>]
ID is unset or already in use - creating new one!
/home/username/.config/Screenlets/CopyStack/default/CopyStack2
[]
LOAD NEW THEME: default
FOUND: /usr/share/screenlets/CopyStack/themes/default
theme.conf found! Loading option-overrides.
theme.conf loaded: 
Name: Bars
Author: RYX (aka Rico Pfaus)
Version: 1.0
Info: A simple theme for the copystack.
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
Screenlet has been initialized.
[<__main__.UrlElement object at 0x240e5d0>]
```

I would imagine that it has something to do with "Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.CopyStack was not provided by any .service files".  

Note: I have tried completely uninstalling screenlets and reinstalling it.  

Thanks in advance for the help!

---

### Post by drmichael on 2010-10-16
[SOLVED]

Nevermind.  It turns out that each screenlet would launch into the far upper-left corner of my display, right behind the menu bar and I couldn't see them.

---

