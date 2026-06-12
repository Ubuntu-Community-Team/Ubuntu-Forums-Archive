---
title: "Run terminal command at startup?"
date: 2011-06-20
forum: General Help
---

### Post by shadowninty on 2011-06-20
Well, I want to run a terminal command at startup. I Google searched, but all the threads were ~5 years old.
The command I want to run is ```
synclient TapButton2=2
synclient TapButton3=3
```

Thanks! :D

---

### Post by Toz on 2011-06-20
If you want to run this for all users, then add it to **/etc/rc.local** prior to the **exit 0** command.

If you want to run this for just your login, have a look at the following instructions for running a program at login: [http://techotopia.com/index.php/Ubuntu_11.04_Unity_Desktop_-_Starting_Applications_on_Login]("http://techotopia.com/index.php/Ubuntu_11.04_Unity_Desktop_-_Starting_Applications_on_Login")

To execute both of those commands on one command line entry, use the following command:```
synclient TapButton2=2 && synclient TapButton3=3
```

---

### Post by shadowninty on 2011-06-21
Thanks for your help! :)

---

### Post by shadowninty on 2011-06-21
Didnt work :(

---

### Post by veggen on 2011-06-21
What did you do? You were offered more than one option.

---

### Post by shadowninty on 2011-06-21
> **veggen said:**
> What did you do? You were offered more than one option.

The first option

my rc.local
```
amb'#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

synclient TapButton2=2 && synclient TapButton3=3
synclient VertTwoFingerScroll=1 && synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5 && synclient EmulateTwoFingerMinZ=48

exit 0
```

---

### Post by prodigy_ on 2011-06-21
Won't work from **rc.local** because synclient tries to connect to X Server and **rc.local** is executed before X Server starts.

---

### Post by shadowninty on 2011-06-21
I added this command to startup applications - no luck
```
synclient TapButton2=2 && synclient TapButton3=3
```

Thanks for your help guys, shame there is not a Thanks button :L

---

### Post by Toz on 2011-06-21
@prodigy - nice catch.

OP: try adding the commands to the .xprofile file in your home directory (creating if necessary):
```
gedit ~/.xprofile
```With contents:
> synclient TapButton2=2
synclient TapButton3=3

And make the file executable:
```
chmod +x ~/.xprofile
```

---

### Post by shadowninty on 2011-06-21
Thank you. Will test out when I'm finished compiling CyanogenMod7

EDIT: Not working :( Sorry

---

### Post by Toz on 2011-06-21
Try changing ~/.xprofile to read:
```
(sleep 3s && synclient TapButton2=2 && synclient TapButton3=3)&
```

Can you also post back the results of:```
ls -l ~ | grep xprofile
```

---

### Post by shadowninty on 2011-06-22
Doesnt return anything [ls -l ~ | grep xprofile]

---

### Post by Toz on 2011-06-22
Sorry, my bad:```
ls -al ~ | grep xprofile
```

Does it work with this change to the .xprofile file?> (sleep 3s && synclient TapButton2=2 && synclient TapButton3=3)&

---

### Post by shadowninty on 2011-06-22
> **Toz said:**
> Sorry, my bad:```
ls -al ~ | grep xprofile
```

Does it work with this change to the .xprofile file?

Didnt work :(

Heres the output from the commnad :)
```
-rwxr-xr-x  1 ciaran ciaran    111 2011-06-21 16:58 .xprofile
```

---

### Post by Toz on 2011-06-22
??? 
Can you run the command:```
(sleep 3s && synclient TapButton2=2 && synclient TapButton3=3)
```from the command line and see if it works?

---

### Post by shadowninty on 2011-06-22
> **Toz said:**
> ??? 
Can you run the command:```
(sleep 3s && synclient TapButton2=2 && synclient TapButton3=3)
```from the command line and see if it works?

It works

---

### Post by Toz on 2011-06-22
This is odd. Can you change your .xprofile file to this:
```
echo "Before command" > ~/.xprofile.log
(sleep 3s && synclient TapButton2=2 && synclient TapButton3=3) >> ~/.xprofile.log
echo "After command" >> ~/.xprofile.log
```

Log out and back in again, and post back the contents of **~/.xprofile.log** and **~/.xsession-errors**

---

### Post by shadowninty on 2011-06-23
> **Toz said:**
> This is odd. Can you change your .xprofile file to this:
```
echo "Before command" > ~/.xprofile.log
(sleep 3s && synclient TapButton2=2 && synclient TapButton3=3) >> ~/.xprofile.log
echo "After command" >> ~/.xprofile.log
```

Log out and back in again, and post back the contents of **~/.xprofile.log** and **~/.xsession-errors**
.log;
```
Before command
After command
```

errors
[hide]```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_IE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-eNNNnO
GNOME_KEYRING_CONTROL=/tmp/keyring-eNNNnO
SSH_AUTH_SOCK=/tmp/keyring-eNNNnO/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-eNNNnO
SSH_AUTH_SOCK=/tmp/keyring-eNNNnO/ssh
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Invalid command: &&
Invalid command: synclient
Starting Dropbox...Initializing opengl options...done
Initializing decor options...done
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.7
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing nautilus-open-terminal extension
** (nm-applet:19336): DEBUG: old state indicates that this was not a disconnect 0
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
** (nm-applet:19336): DEBUG: foo_client_state_changed_cb
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
** Message: Initializing gksu extension...
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done

** (process:19331): WARNING **: recent-manager-provider.vala:125: Desktop file for ark was not found
** (process:19331): DEBUG: zeitgeist-datahub.vala:174: Inserting 13 events
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done

(nautilus:19330): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Initializing scale options...done
I/O warning : failed to load external entity "/home/ciaran/.compiz/session/10e33a4e96752603e5130882398836791300000192470036"
Initializing session options...done
Dropbox isn't running!
Done!
** (<unknown>:19315): DEBUG: Unity accessibility initialization
** (<unknown>:19315): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1366x768

unity-panel-service: no process found
** (<unknown>:19315): DEBUG: PanelController:: Added Panel for Monitor 0
** (nm-applet:19336): DEBUG: foo_client_state_changed_cb
Initializing unityshell options...done
Starting unity-window-decorator
** (<unknown>:19315): DEBUG: PlaceEntry: Applications
** (<unknown>:19315): DEBUG: PlaceEntry: Commands
** (<unknown>:19315): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:19315): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:19315): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:19315): DEBUG: Setting to primary screen rect: x=0 y=0 w=1366 h=768
** (<unknown>:19315): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:19315): DEBUG: TrayChild Rejected: dropbox dropbox Dropbox
** (<unknown>:19315): DEBUG: TrayChild Rejected: nm-applet nm-applet Nm-applet

** (gnome-screensaver:19531): WARNING **: screensaver already running in this session

(<unknown>:19315): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:19315): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:19315): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:19315): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:19315): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:19315): DEBUG: IndicatorAdded: libme.so
** (<unknown>:19315): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (<unknown>:19315): DEBUG: Connected to proxy
** (<unknown>:19315): DEBUG: Connected to proxy

(<unknown>:19315): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:19315): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:19315): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:19315): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:19315): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:19315): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
** (process:19331): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:19331): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:19315): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (<unknown>:19315): DEBUG: TrayChild Rejected: Opera opera OperaNext
** (<unknown>:19315): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
** (process:19331): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:19315): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:19315): DEBUG: Connected to proxy
** (<unknown>:19315): DEBUG: MaximizeIfBigEnough: Gedit window size doesn't fit
** (<unknown>:19315): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:19315): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:19315): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:19315): DEBUG: TrayChild Rejected: (null) (null) (null)

** (<unknown>:19315): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:19315): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:19315): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:19315): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:19315): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:19315): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:19315): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:19315): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (<unknown>:19315): DEBUG: MaximizeIfBigEnough: Gedit window size doesn't fit

** (<unknown>:19315): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:19315): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:19315): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:19315): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:19315): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:19315): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:19315): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:19315): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (deja-dup-monitor:19333): DEBUG: monitor.vala:282: Late by 40509 seconds.  Backing up now.
** (deja-dup-monitor:19333): DEBUG: monitor.vala:278: Waiting 45891 seconds until next backup.

(<unknown>:19315): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 2

(<unknown>:19315): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(<unknown>:19315): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 3

(<unknown>:19315): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID
** (<unknown>:19315): DEBUG: MaximizeIfBigEnough: Gedit window size doesn't fit 
```
[/hide]

---

### Post by Toz on 2011-06-23
We're getting close:> Invalid command: &&
Invalid command: synclient
Lets try this in your .xprofile file:
```
echo "`date` - Before commands" > ~/.xprofile.log
/usr/bin/synclient TapButton2=2 >> ~/.xprofile.log
/usr/bin/synclient TapButton3=3 >> ~/.xprofile.log
echo "`date` - After commands" >> ~/.xprofile.log
```

Post back **~/.xprofile.log**

---

### Post by shadowninty on 2011-06-23
.xprofile.log

```
Thu Jun 23 15:58:07 IST 2011 - Before commands
Thu Jun 23 15:58:07 IST 2011 - After commands
```

---

### Post by Toz on 2011-06-23
Did it work? 
Anything different in .xsession-errors?

---

### Post by shadowninty on 2011-06-23
Didnt work :(
errors;
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_IE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-nvz9wV
SSH_AUTH_SOCK=/tmp/keyring-nvz9wV/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-nvz9wV
SSH_AUTH_SOCK=/tmp/keyring-nvz9wV/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-nvz9wV
SSH_AUTH_SOCK=/tmp/keyring-nvz9wV/ssh
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Starting Dropbox...Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
I/O warning : failed to load external entity "/home/ciaran/.compiz/session/105defbfff825d7a3a130884348057600700000053420035"
Initializing session options...done
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.7
Initializing nautilus-open-terminal extension
** (nm-applet:5445): DEBUG: old state indicates that this was not a disconnect 0
** Message: Initializing gksu extension...
** (nm-applet:5445): DEBUG: foo_client_state_changed_cb

(nautilus:5426): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:5406): DEBUG: Unity accessibility initialization
** (<unknown>:5406): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1366x768

unity-panel-service: no process found
** (<unknown>:5406): DEBUG: PanelController:: Added Panel for Monitor 0

** (process:5430): WARNING **: recent-manager-provider.vala:125: Desktop file for ark was not found
** (process:5430): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
Initializing unityshell options...done
** (<unknown>:5406): DEBUG: PlaceEntry: Applications
** (<unknown>:5406): DEBUG: PlaceEntry: Commands
** (<unknown>:5406): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:5406): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:5406): DEBUG: /com/canonical/unity/filesplace
Starting unity-window-decorator
** (nm-applet:5445): DEBUG: foo_client_state_changed_cb
Dropbox isn't running!
Done!
** (<unknown>:5406): DEBUG: Setting to primary screen rect: x=0 y=0 w=1366 h=768
** (<unknown>:5406): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:5406): DEBUG: TrayChild Rejected: nm-applet nm-applet Nm-applet

(<unknown>:5406): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:5406): DEBUG: TrayChild Rejected: dropbox dropbox Dropbox
** (<unknown>:5406): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:5406): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:5406): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:5406): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:5406): DEBUG: IndicatorAdded: libme.so
** (<unknown>:5406): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (process:5430): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:5406): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:5406): DEBUG: MaximizeIfBigEnough: Gedit window size doesn't fit
```

---

### Post by Toz on 2011-06-23
Maybe it is working and something is re-setting it back before you use it? Try this:
```
#!/bin/bash
echo "`date` - Before commands" > ~/.xprofile.log
sleep 10s
/usr/bin/synclient TapButton2=2 && echo "`date` - 2=2" >> ~/.xprofile.log
/usr/bin/synclient TapButton3=3 && echo "`date` - 3=3" >> ~/.xprofile.log
echo "`date` - After commands" >> ~/.xprofile.log
```

If still not working, try changing delay time longer (ie 30s, 60s, etc)

---

### Post by shadowninty on 2011-06-23
Still doesnt work :( Thanks for your help!

---

### Post by Toz on 2011-06-23
Can I see .xsession-errors and .xprofile.log?

---

### Post by shadowninty on 2011-06-23
log:```
Thu Jun 23 20:21:58 IST 2011 - Before commands
Thu Jun 23 20:22:28 IST 2011 - 2=2
Thu Jun 23 20:22:28 IST 2011 - 3=3
Thu Jun 23 20:22:28 IST 2011 - After commands
```
errors:```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_IE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-BLcIaw
SSH_AUTH_SOCK=/tmp/keyring-BLcIaw/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-BLcIaw
SSH_AUTH_SOCK=/tmp/keyring-BLcIaw/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-BLcIaw
SSH_AUTH_SOCK=/tmp/keyring-BLcIaw/ssh
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Starting Dropbox...I/O warning : failed to load external entity "/home/ciaran/.compiz/session/101980f913d250425d130885694871923500000049450035"
Initializing session options...done

** (process:5026): WARNING **: recent-manager-provider.vala:125: Desktop file for ark was not found
** (process:5026): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.7
Initializing nautilus-open-terminal extension
** Message: Initializing gksu extension...

(nautilus:5021): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (nm-applet:5039): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:5039): DEBUG: foo_client_state_changed_cb
** (<unknown>:5017): DEBUG: Unity accessibility initialization
** (<unknown>:5017): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1366x768

unity-panel-service: no process found
** (<unknown>:5017): DEBUG: PanelController:: Added Panel for Monitor 0
Done!
Initializing unityshell options...done
Starting unity-window-decorator
** (<unknown>:5017): DEBUG: PlaceEntry: Applications
** (<unknown>:5017): DEBUG: PlaceEntry: Commands
** (<unknown>:5017): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:5017): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:5017): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:5017): DEBUG: Setting to primary screen rect: x=0 y=0 w=1366 h=768
** (<unknown>:5017): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:5017): DEBUG: TrayChild Rejected: nm-applet nm-applet Nm-applet
** (<unknown>:5017): DEBUG: TrayChild Rejected: gnome-power-manager gnome-power-manager Gnome-power-manager
** (<unknown>:5017): DEBUG: TrayChild Rejected: dropbox dropbox Dropbox
** (nm-applet:5039): DEBUG: foo_client_state_changed_cb

(<unknown>:5017): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (gnome-screensaver:5248): WARNING **: screensaver already running in this session
** (<unknown>:5017): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:5017): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:5017): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:5017): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:5017): DEBUG: IndicatorAdded: libme.so
** (<unknown>:5017): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (process:5026): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:5017): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:5017): DEBUG: MaximizeIfBigEnough: Gedit window size doesn't fit
```

---

### Post by LordNeo on 2011-06-23
Startup applications ->

bash -c "blablablabla"

then add the second as a new entry, because the && will not let the second one start until the first one is finished

---

### Post by shadowninty on 2011-06-23
should I put it ""?

---

### Post by LordNeo on 2011-06-23
Yup, i use it to start conky.
In my case it's something like:

bash -c "sleep 10; conky"

You could try using:

bash -c "synclient TapButton2=2; synclient TapButton3=3"

That should do both commands in the same order. You could add "sleep xxx;" if you feel you may need it (some other program has load before)

Screenshot: [http://i39.photobucket.com/albums/e173/LordNeoZ/Pantallazo-5.png](http://i39.photobucket.com/albums/e173/LordNeoZ/Pantallazo-5.png)

---

### Post by shadowninty on 2011-06-23
> **LordNeo said:**
> Yup, i use it to start conky.
In my case it's something like:

bash -c "sleep 10; conky"

You could try using:

bash -c "synclient TapButton2=2; synclient TapButton3=3"

That should do both commands in the same order. You could add "sleep xxx;" if you feel you may need it (some other program has load before)

Screenshot: [http://i39.photobucket.com/albums/e173/LordNeoZ/Pantallazo-5.png](http://i39.photobucket.com/albums/e173/LordNeoZ/Pantallazo-5.png)

I can't put into words how much I love you. Thank you so much!!!! &#9829;

---

### Post by LordNeo on 2011-06-23
Glad to help :D!

---

