---
title: "Natty gnome-settings-daemon crashes on login"
date: 2011-05-07
forum: General Help
---

### Post by kenfeyl on 2011-05-07
Hi everyone,

I just upgraded to amd64 natty and am suddenly having a problem with gnome-settings-daemon. Whenever I log in, gnome-settings-daemon lasts for about 10 seconds before crashing. I know that it has crashed because the themes suddenly disappear and I get the dreaded gray bar across the top. Where do I look to debug this?

The output of .xsession-errors is pasted below. Not sure what to make of it, except that I see lots of errors thrown by dBus and Glib. Not sure if that's significant. I should mention that "sudo gnome-settings-daemon" does successfully turn it back on, but this doesn't seem to turn it fully on (e.g., right-clicking on the desktop still pops up a gray menu).

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-r5knDh
SSH_AUTH_SOCK=/tmp/keyring-r5knDh/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-r5knDh
SSH_AUTH_SOCK=/tmp/keyring-r5knDh/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-r5knDh
SSH_AUTH_SOCK=/tmp/keyring-r5knDh/ssh

** (gnome-settings-daemon:2000): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:2000): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.
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
I/O warning : failed to load external entity "/home/kevin/.compiz/session/10e59f9a67341da9c130481159866623200000019430030"
Initializing session options...done
** (nm-applet:2037): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2037): DEBUG: old state indicates that this was not a disconnect 0
** (<unknown>:2014): DEBUG: Unity accessibility initialization
** (<unknown>:2014): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

Initializing nautilus-gdu extension

(nautilus:2036): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
unity-panel-service: no process found
** (<unknown>:2014): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:2014): DEBUG: PlaceEntry: Applications
** (<unknown>:2014): DEBUG: PlaceEntry: Commands
** (<unknown>:2014): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:2014): DEBUG: /com/canonical/unity/applicationsplace
Starting unity-window-decorator
** (<unknown>:2014): DEBUG: /com/canonical/unity/filesplace
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (<unknown>:2014): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=800
** (<unknown>:2014): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:2014): DEBUG: TrayChild Rejected: nm-applet nm-applet Nm-applet
** (<unknown>:2014): DEBUG: Connected to proxy

** (gnome-screensaver:2177): WARNING **: screensaver already running in this session
** (<unknown>:2014): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:2014): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:2014): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:2014): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:2014): DEBUG: IndicatorAdded: libme.so
** (<unknown>:2014): DEBUG: IndicatorAdded: libsession.so
** (<unknown>:2014): DEBUG: Connected to proxy
** (<unknown>:2014): DEBUG: Connected to proxy

(<unknown>:2014): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:2014): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:2014): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:2014): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:2014): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:2014): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"

** (nm-applet:2037): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:2037): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/0
** Message: <info>  No keyring secrets found for Auto DeborahIsBeautiful/802-11-wireless-security; asking user.


** (nm-applet:2037): WARNING **: applet.c.2882 (applet_settings_new_secrets_requested_cb): couldn't find details for connection
** Message: <info>  No keyring secrets found for Auto DeborahIsBeautiful/802-11-wireless-security; asking user.

** (nm-applet:2037): DEBUG: foo_client_state_changed_cb
** (nm-applet:2037): DEBUG: going for offline with icon: notification-network-wireless-disconnected

** (<unknown>:2014): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:2014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:2014): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:2014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:2014): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (nm-applet:2037): DEBUG: foo_client_state_changed_cb

** (<unknown>:2014): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:2014): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:2014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:2014): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:2014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:2014): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:2043): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
python: can't open file '/usr/share/gnome-panel/add-indicator-applet.py': [Errno 2] No such file or directory
** (<unknown>:2014): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
/usr/lib/python2.7/dist-packages/UpdateManager/SimpleGtkbuilderApp.py:35: GtkWarning: Ignoring the separator setting
  self.builder.add_from_file(path)
** (<unknown>:2014): DEBUG: MaximizeIfBigEnough: Firefox window size doesn't fit

(firefox-bin:2337): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
No bp log location saved, using default.
[000:066] Browser XEmbed support present: 1
[000:067] Browser toolkit is Gtk2.
[000:067] Using Gtk2 toolkit
[000:113] Warning(clientchannel.cc:553): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[000:136] Warning(clientchannel.cc:396): Could not initiate GoogleTalkPlugin connection
[000:136] Warning(optionsfile.cc:22): Load: Could not open file
[000:136] Warning(clientchannel.cc:523): Failed to get GoogleTalkPlugin path. Trying default.
[000:139] Started GoogleTalkPlugin, path=/opt/google/talkplugin/GoogleTalkPlugin
[000:139] Waiting for GoogleTalkPlugin to start...
[001:171] Warning(clientchannel.cc:553): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
[006:499] Warning(clientchannel.cc:396): Could not initiate GoogleTalkPlugin connection
[006:499] Waiting for GoogleTalkPlugin to start...
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
[007:501] Read port file, port=48052
[007:561] Initiated connection to GoogleTalkPlugin
[007:602] Socket connection established
[007:602] ScheduleOnlineCheck: Online check in 5000ms
[007:702] Got cookie response, socket is authorized
[007:702] AUTHORIZED; socket handshake complete
** (process:2043): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:2014): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:2014): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
WARNING:root:timeout reached, exiting
  PID TTY          TIME CMD
 2017 ?        00:00:00 pulseaudio
** (<unknown>:2014): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
[012:603] HandleOnlineCheck: Starting check
[012:603] HandleOnlineCheck: OK; current state: 3
Gtk-Message: Failed to load module "gnomesegvhandler"

(<unknown>:2014): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (process:2043): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (gnome-session:1943): DEBUG: GsmXsmpServer: accept_ice_connection()
** (gnome-session:1943): DEBUG: GsmXsmpServer: auth_ice_connection()
** (gnome-session:1943): DEBUG: GsmXSMPClient: Setting up new connection
** (gnome-session:1943): DEBUG: GsmXSMPClient: New client '0xb63c90 []'
** (gnome-session:1943): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/Client9 to store
** (gnome-session:1943): DEBUG: GsmManager: Client added: /org/gnome/SessionManager/Client9
** (gnome-session:1943): DEBUG: GsmXSMPClient: Initializing client 0xb63c90 []
** (gnome-session:1943): DEBUG: GsmXSMPClient: Client '0xb63c90 []' received RegisterClient(NULL)
** (gnome-session:1943): DEBUG: GsmManager: Adding new client 10e59f9a67341da9c13048117698931800000019430036 to session
** (gnome-session:1943): DEBUG: GsmXSMPClient: Sending RegisterClientReply to '0xb63c90 [10e59f9a67341da9c13048117698931800000019430036]'
** (gnome-session:1943): DEBUG: GsmXSMPClient: Sending initial SaveYourself
** (gnome-session:1943): DEBUG: GsmXSMPClient: Set properties from client '0xb63c90 [10e59f9a67341da9c13048117698931800000019430036]'
** (gnome-session:1943): DEBUG: GsmXSMPClient:   CurrentDirectory = '/home/kevin'
** (gnome-session:1943): DEBUG: GsmXSMPClient: Set properties from client '0xb63c90 [10e59f9a67341da9c13048117698931800000019430036]'
** (gnome-session:1943): DEBUG: GsmXSMPClient:   ProcessID = '2624'
** (gnome-session:1943): DEBUG: GsmXSMPClient: Set properties from client '0xb63c90 [10e59f9a67341da9c13048117698931800000019430036]'
** (gnome-session:1943): DEBUG: GsmXSMPClient:   Program = 'thunderbird-bin'
** (gnome-session:1943): DEBUG: GsmXSMPClient: Set properties from client '0xb63c90 [thunderbird-bin 10e59f9a67341da9c13048117698931800000019430036]'
** (gnome-session:1943): DEBUG: GsmXSMPClient:   CloneCommand = 'thunderbird-bin' 
** (gnome-session:1943): DEBUG: GsmXSMPClient: Set properties from client '0xb63c90 [thunderbird-bin 10e59f9a67341da9c13048117698931800000019430036]'
** (gnome-session:1943): DEBUG: GsmXSMPClient:   RestartCommand = 'thunderbird-bin' '--sm-client-id' '10e59f9a67341da9c13048117698931800000019430036' '--screen' '0' 
** (gnome-session:1943): DEBUG: GsmXSMPClient: Set properties from client '0xb63c90 [thunderbird-bin 10e59f9a67341da9c13048117698931800000019430036]'
** (gnome-session:1943): DEBUG: GsmXSMPClient:   UserID = 'kevin'
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmXSMPClient: Client '0xb63c90 [thunderbird-bin 10e59f9a67341da9c13048117698931800000019430036]' received SaveYourselfDone(success = True)
** (gnome-session:1943): DEBUG: GsmXsmpServer: sms_error_handler (0xbad110, FALSE, 3, 9, 32771, 0)
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (process:2043): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged

** (<unknown>:2014): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:2014): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:2014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:2014): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:2014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:2014): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:2043): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged

** (<unknown>:2014): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:2014): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:2014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:2014): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:2014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:2014): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1943): DEBUG: GsmXsmpServer: accept_ice_connection()
** (gnome-session:1943): DEBUG: GsmXsmpServer: auth_ice_connection()
** (gnome-session:1943): DEBUG: GsmXSMPClient: Setting up new connection
** (gnome-session:1943): DEBUG: GsmXSMPClient: New client '0xb63d30 []'
** (gnome-session:1943): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/Client10 to store
** (gnome-session:1943): DEBUG: GsmManager: Client added: /org/gnome/SessionManager/Client10
** (gnome-session:1943): DEBUG: GsmXSMPClient: Initializing client 0xb63d30 []
** (gnome-session:1943): DEBUG: GsmXSMPClient: Client '0xb63d30 []' received RegisterClient(NULL)
** (gnome-session:1943): DEBUG: GsmManager: Adding new client 10e59f9a67341da9c130481192896189700000019430037 to session
** (gnome-session:1943): DEBUG: GsmXSMPClient: Sending RegisterClientReply to '0xb63d30 [10e59f9a67341da9c130481192896189700000019430037]'
** (gnome-session:1943): DEBUG: GsmXSMPClient: Sending initial SaveYourself
** (gnome-session:1943): DEBUG: GsmXSMPClient: Set properties from client '0xb63d30 [10e59f9a67341da9c130481192896189700000019430037]'

```

---

