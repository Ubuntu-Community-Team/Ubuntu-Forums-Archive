---
title: "Graphical problems each time I open my session..."
date: 2010-10-22
forum: General Help
---

### Post by nandayo on 2010-10-22
Hi all,

Without any obvious reason, my computer (under lucid) decided to have strange problems at each session opening... here are the problems:

- mouse cursor is a cross
- windows are strange, they have no borders ! 
- No multiple desktop, no screenlets...
- Windows have a strange behavior : cannote be reduced, I can't supperpose 2 windows etc.

The only "solution" I found is to go in the application "Appearence", then I see that visual effects are disabled, I activate them, and then everything goes back to normal (until the next time I start...). And if I disable visual effects after everything went back to normal, everything stills OK,e ven without visual effects... then this is *only* at new session start that there is a problem...

Here is what I can see in my Xerrors.log
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=fr_FR.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[1831]: EggSMClient-WARNING: Desktop file '/home/emmanuel/.config/autostart/skype-1.desktop' has malformed Icon key 'skype.png'(should not include extension)
GNOME_KEYRING_CONTROL=/tmp/keyring-8hJlqR
GNOME_KEYRING_PID=1877
GNOME_KEYRING_CONTROL=/tmp/keyring-8hJlqR
GNOME_KEYRING_CONTROL=/tmp/keyring-8hJlqR
SSH_AUTH_SOCK=/tmp/keyring-8hJlqR/ssh
** Message: adding killswitch idx 1 state 1
** Message: killswitch 1 is 1
** Message: killswitches state 1
** Message: killswitch 1 is 1
** Message: killswitches state 1
gnome-session[1831]: WARNING: Could not launch application 'ubuntuone-client-applet.desktop': Unable to start application: L'exécution du processus fils «*ubuntuone-client-applet*» a échoué (Aucun fichier ou dossier de ce type)
gnome-session[1831]: WARNING: Could not launch application 'lanuchy.desktop': Unable to start application: L'exécution du processus fils «*lanuchy*» a échoué (Aucun fichier ou dossier de ce type)

(polkit-gnome-authentication-agent-1:1930): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1930): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (nm-applet:1932): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension
** Message: Initializing gksu extension...
CachingBackend: Chargement des instances depuis le cache
CachingBackend: Chargement de <ClearWeather2>
CachingBackend: Chargement de <ClearWeather1>
CachingBackend: Chargement des instances depuis le cache
CachingBackend: Chargement de <AppMenu1>
CachingBackend: Chargement des instances depuis le cache
CachingBackend: Chargement de <Terminal1>
No global tempdir found, creating new one.
Temp directory /tmp/screenlets created.
Creating new entry for ClearWeatherScreenlet in /tmp/screenlets/screenlets.emmanuel.running
Chargement des instances dans: /home/emmanuel/.config/Screenlets/ClearWeather/default/
Fichier: ClearWeather2.ini

** (nautilus:1902): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:1902): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:1902): WARNING **: Can not get _NET_WORKAREA

** (nautilus:1902): WARNING **: Can not determine workarea, guessing at layout
Traceback (most recent call last):
  File "/usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py", line 581, in <module>
    screenlets.session.create_session(ClearWeatherScreenlet)
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 472, in create_session

(gnome-settings-daemon:1881): GLib-GObject-WARNING **: IA__g_object_notify: object class `GkbdStatus' has no property named `name'
    session.start()
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 237, in start
    if self.__load_instances():
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 391, in __load_instances
    sl = self.create_instance(id=filename[:-4], enable_saving=False)
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 143, in create_instance
    sl = self.screenlet(id=id, session=self, **keyword_args)
  File "/usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py", line 67, in __init__
    screenlets.Screenlet.__init__(self, width=int(132 * self.scale), height=int(100 * self.scale),uses_theme=True, **keyword_args) 
  File "/usr/lib/pymodules/python2.6/screenlets/__init__.py", line 808, in __init__
Trouvé une session en cours de AppMenu, ajout d'une nouvelle instance par service.
Erreur dans screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.AppMenu was not provided by any .service files
    if str(sensors.sys_get_window_manager()).lower() == 'kwin':
  File "/usr/lib/pymodules/python2.6/screenlets/sensors.py", line 340, in sys_get_window_manager
Trouvé une session en cours de Terminal, ajout d'une nouvelle instance par service.
Erreur dans screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.Terminal was not provided by any .service files
    name = win.property_get("_NET_WM_NAME")[2]
AttributeError: 'str' object has no attribute 'property_get'
Screenlet has already been added to /tmp/screenlets/screenlets.emmanuel.running
Chargement des instances dans: /home/emmanuel/.config/Screenlets/Terminal/default/
Fichier: Terminal1.ini
Screenlet has already been added to /tmp/screenlets/screenlets.emmanuel.running
Chargement des instances dans: /home/emmanuel/.config/Screenlets/AppMenu/default/
Fichier: AppMenu1.ini

(gnome-power-manager:1907): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x164d2c0'
Traceback (most recent call last):
  File "/home/emmanuel/.screenlets/Terminal/TerminalScreenlet.py", line 277, in <module>
    screenlets.session.create_session(TerminalScreenlet)
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 472, in create_session
    session.start()
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 237, in start
    if self.__load_instances():
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 391, in __load_instances
    sl = self.create_instance(id=filename[:-4], enable_saving=False)
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 143, in create_instance
    sl = self.screenlet(id=id, session=self, **keyword_args)
  File "/home/emmanuel/.screenlets/Terminal/TerminalScreenlet.py", line 53, in __init__
    screenlets.Screenlet.__init__(self, is_widget=False, width=640, height=480, uses_theme=False, **keyword_args)
  File "/usr/lib/pymodules/python2.6/screenlets/__init__.py", line 808, in __init__
    if str(sensors.sys_get_window_manager()).lower() == 'kwin':
  File "/usr/lib/pymodules/python2.6/screenlets/sensors.py", line 340, in sys_get_window_manager
    name = win.property_get("_NET_WM_NAME")[2]
AttributeError: 'str' object has no attribute 'property_get'
Traceback (most recent call last):
  File "/usr/share/screenlets/AppMenu/AppMenuScreenlet.py", line 344, in <module>
    screenlets.session.create_session(AppMenuScreenlet)
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 472, in create_session
    session.start()
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 237, in start
    if self.__load_instances():
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 391, in __load_instances
    sl = self.create_instance(id=filename[:-4], enable_saving=False)
  File "/usr/lib/pymodules/python2.6/screenlets/session.py", line 143, in create_instance
    sl = self.screenlet(id=id, session=self, **keyword_args)
  File "/usr/share/screenlets/AppMenu/AppMenuScreenlet.py", line 55, in __init__
    uses_theme=True,ask_on_option_override = False,  **keyword_args)
  File "/usr/lib/pymodules/python2.6/screenlets/__init__.py", line 808, in __init__
    if str(sensors.sys_get_window_manager()).lower() == 'kwin':
  File "/usr/lib/pymodules/python2.6/screenlets/sensors.py", line 340, in sys_get_window_manager
    name = win.property_get("_NET_WM_NAME")[2]
AttributeError: 'str' object has no attribute 'property_get'
** (nm-applet:1932): DEBUG: foo_client_state_changed_cb
** (nm-applet:1932): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 43053 1286834400 1286791347
evolution-alarm-notify-Message:  Tue Oct 12 00:00:00 2010

evolution-alarm-notify-Message:  Mon Oct 11 12:02:27 2010

evolution-alarm-notify-Message: Setting timeout for 30449 1286821800 1286791351
evolution-alarm-notify-Message:  Mon Oct 11 20:30:00 2010

evolution-alarm-notify-Message:  Mon Oct 11 12:02:31 2010

evolution-alarm-notify-Message: Setting timeout for 30449 1286821800 1286791351
evolution-alarm-notify-Message:  Mon Oct 11 20:30:00 2010

evolution-alarm-notify-Message:  Mon Oct 11 12:02:31 2010

** (update-notifier:2355): DEBUG: Skipping reboot required
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

```

We can see that there are many problems with desktops, screenlets etc.

If someone have an idea... :-/

Thanks !

---

