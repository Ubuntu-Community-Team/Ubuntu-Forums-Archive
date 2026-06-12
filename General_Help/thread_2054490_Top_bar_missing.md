---
title: "Top bar missing"
date: 2012-09-07
forum: General Help
---

### Post by Kreacher on 2012-09-07
Unity breaks too easy.

The side bar with all the icons is there. It works fine. Autohides and everything.

The top bar (panel) with the clock, logout and all the other stuff is gone, missing, not there at all. How do I get that back? 

Reinstalling Unity doesn't help.
unity --reset doesn't help.
unity --replace doesn't help

Yes, unity plugin is enabled.

Thanks!

---

### Post by cryptotheslow on 2012-09-07
Is unity-panel-service running?

Try:
```
ps aux | grep panel
```

You should see something like:
```
crypto    2131  0.0  0.5 595476 22044 ?        Sl   13:18   0:06 /usr/lib/unity/unity-panel-service
crypto    3227  0.0  0.0  13584   928 pts/0    S+   18:18   0:00 grep --color=auto panel
```

---

### Post by Kreacher on 2012-09-07
Results:

kreacher  5527  0.0  0.0   4620   788 pts/0    S+   12:23   0:00 grep --color=auto panel

---

### Post by cryptotheslow on 2012-09-07
That would be why the panel isn't showing then :)

Is it still installed?

What do these result in?
```
dpkg-query -L unity-services
```
```
apt-cache policy unity-services
```

---

### Post by Kreacher on 2012-09-07
Sounds reasonable to me, Thanks! :)  Here are the results:

```
/.
/usr
/usr/share
/usr/share/dbus-1
/usr/share/dbus-1/services
/usr/share/dbus-1/services/com.canonical.Unity.Panel.Service.service
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/unity-panel-service.1.gz
/usr/share/doc
/usr/share/doc/unity-services
/usr/share/doc/unity-services/copyright
/usr/share/doc/unity-services/changelog.Debian.gz
/usr/lib
/usr/lib/unity
/usr/lib/unity/unity-panel-service

``````
unity-services:
  Installed: 5.14.0-0ubuntu1
  Candidate: 5.14.0-0ubuntu1
  Version table:
 *** 5.14.0-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     5.10.0-0ubuntu6 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages

```

---

### Post by cryptotheslow on 2012-09-07
Looks to be right.

Can you start it manually from a terminal with this?
```
/usr/lib/unity/unity-panel-service
```

Even if it doesn't start you'll get some idea why it is erroring.

---

### Post by Kreacher on 2012-09-07
I'd say it is sick:

```
(unity-panel-service:7042): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(unity-panel-service:7042): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(unity-panel-service:7042): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(unity-panel-service:7042): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

** (unity-panel-service:7042): WARNING **: on_indicator_menu_show() called with a NULL entry

(unity-panel-service:7042): IDO-CRITICAL **: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed

(unity-panel-service:7042): LIBDBUSMENU-GLIB-WARNING **: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/printers

```

I should mention that I am using the 2d Unity since my video card doesn't support the 3d.

---

### Post by cryptotheslow on 2012-09-07
Ignore this - just saw you are using 2D!

---

### Post by cryptotheslow on 2012-09-07
OK, on 2D the command:
```
ps aux | grep panel
```

Should show both unity-panel-service and unity-2d-panel running:
crypto    3875  1.0  0.7 686772 30024 ?        Sl   19:14   0:00 unity-2d-panel
crypto    3939  2.0  0.4 519648 19144 ?        Sl   19:14   0:00 /usr/lib/unity/unity-panel-service
crypto    4166  0.0  0.0  13584   928 pts/0    S+   19:15   0:00 grep --color=auto panel


Have you installed any addition Compiz plugins or otherwise tweaked things using something like CCSM?

You could try resetting all the Compiz setting using:
```
dconf reset -f /org/compiz/
```

You need to logout and back in to restart Compiz for that to take effect.

---

### Post by Kreacher on 2012-09-07
> **cryptotheslow said:**
> OK, on 2D the command:
```
ps aux | grep panel
```Should show both unity-panel-service and unity-2d-panel running:
crypto    3875  1.0  0.7 686772 30024 ?        Sl   19:14   0:00 unity-2d-panel
crypto    3939  2.0  0.4 519648 19144 ?        Sl   19:14   0:00 /usr/lib/unity/unity-panel-service
crypto    4166  0.0  0.0  13584   928 pts/0    S+   19:15   0:00 grep --color=auto panel


Have you installed any addition Compiz plugins or otherwise tweaked things using something like CCSM?

You could try resetting all the Compiz setting using:
```
dconf reset -f /org/compiz/
```You need to logout and back in to restart Compiz for that to take effect.

Results for 
ps aux | grep panel:

```
kreacher 12805  0.0  0.0   4620   788 pts/0    S+   13:32   0:00 grep --color=auto panel
```I installed dconf and the dconf-tools since they were not installed. Then I reset compiz, logged out and back in as instructed.

Yes, I did install the compiz CCSM, That's when I started having problems. All my fault, I'm sure. Just need to fix it. The reset of compiz didn't help.

---

### Post by cryptotheslow on 2012-09-07
Can you try starting unity-2d-panel from the command line and see what errors it gives?

---

### Post by Kreacher on 2012-09-07
I'm not sure how to start the panel, but here is what I got using unity-2d-panel as the command in terminal:
```
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0
unity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F10" 
unity-2d-panel: [WARNING] void GnomeSessionClient::slotRegisterClientFinished(QDBusPendingCallWatcher*): Failed to register with GnomeSession: "The name org.gnome.SessionManager was not provided by any .service files" 
unity-2d-panel: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window41943042") 
unity-2d-panel: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application555378160") 
unity-2d-panel: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window41943042") 
unity-2d-panel: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application555378160")

```
Note: this is a partial result since the thing seems to have stopped displaying information.

---

### Post by cryptotheslow on 2012-09-07
You could try creating a new user account and login using that. If that works fine then at least you know it is just something to do with the settings on your usual account rather than something system related.

---

### Post by Kreacher on 2012-09-07
You are on the right track. A guest session works fine.

---

### Post by cryptotheslow on 2012-09-07
Well this will reset everything to defaults
```
dconf reset -f /
```

It might be a bit of an overkill though!

You could also try renaming these folders in your home directory before logging out and back in to recreate them from scratch:
.gconf
.gnome2
.metacity  (if it exists)

---

### Post by Kreacher on 2012-09-07
> **cryptotheslow said:**
> Well this will reset everything to defaults
```
dconf reset -f /
```It might be a bit of an overkill though!

You could also try renaming these folders in your home directory before logging out and back in to recreate them from scratch:
.gconf
.gnome2
.metacity  (if it exists)
Sadly, none of this helped.

Oddly enough, if I try to start the unity-2d-panel it tries to start. The errors stop showing and I do not get the command prompt back until I close the terminal or <ctrl> c. At that time, the panel disappears again. 

I di create a new user and everything seems to work fine there. Is there a way to remove my admin account and use the other one as admin? I think i know how. Just want to be sure.

Thanks for all of your assistance.

---

### Post by cryptotheslow on 2012-09-07
Sure - just use the User Accounts application from the dash to create a new user and set its type as Administrator rather than Standard.

Login to the new user and copy any files that you want to keep over from the old user's home directory. Make sure your sudo access works on the new account, then just delete the original in User Accounts.

You may need to change the ownership on the files you copy over from one account to the other.

```
sudo chown *newusername:newusername filename*
```

or for a whole directory
```
sudo chown -R *newusername:newusername directoryname*
```

---

### Post by Kreacher on 2012-09-07
Sounds like a plan. Thank you again.

---

