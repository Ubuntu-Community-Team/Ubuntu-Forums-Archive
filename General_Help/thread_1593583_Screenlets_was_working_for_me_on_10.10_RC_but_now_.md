---
title: "Screenlets was working for me on 10.10 RC but now doesn't with the official 10.10"
date: 2010-10-11
forum: General Help
---

### Post by pbajoswb on 2010-10-11
I got into using screenlets on the Maverick RC and was looking forward to using them again when the official release came out.

However when I try and invoke them from the Accessories menu the dialog briefly pops up before disappearing. It's not even on the screen long enough to draw the dialogs contents.

It tried entering "screenlets" at the terminal and I get this....


** (screenlets-manager.py:1741): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (screenlets-manager.py:1741): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (screenlets-manager.py:1741): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
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
True
Create autostarter for: Screenlets Daemon
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 1308, in <module>
    app = ScreenletsManager()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 104, in __init__
    utils.lookup_daemon_autostart()
  File "/usr/lib/pymodules/python2.6/screenlets/utils.py", line 519, in lookup_daemon_autostart
    f = open(starter, 'w')
IOError: [Errno 13] Permission denied: '/home/username/.config/autostart/Screenlets Daemon.desktop'


I've tried looking up Gflags and anything else I can think of with no luck.

Does anyone know what I did wrong?

---

### Post by pbajoswb on 2010-10-15
Update:

After fumbling around for a while I decided to start again from scratch.

I redid the partitions and reloaded Ubuntu fresh from the CD.

With that done, I checked and Screenlets worked.

Now, I have an script I use to load my favorite apps and remove the ones I don't need. Basically, its a collection of "apt-get install"s and "apt-get remove"s. I watched carefully this time, and saw a number of error references to ubuntuzilla. I had a couple of old lines from way back for ubuntuzilla and had never removed them.

I removed those lines from the script. Followed the suggests from the error messages to run "apt-get -f install". And then reran the script.

Now everything works.

---

### Post by Nonplay on 2010-10-17
Maybe the folder autostart is owned by the root.
Try changing the owner:

```
sudo chown $(whoami) ~/.config/autostart
```

---

