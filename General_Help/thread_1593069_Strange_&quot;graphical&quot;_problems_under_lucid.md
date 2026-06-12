---
title: "Strange &quot;graphical&quot; problems under lucid without any reason..."
date: 2010-10-11
forum: General Help
---

### Post by nandayo on 2010-10-11
Hi all,

I'm still under lucid 64 bits, and this morning when I booted my laptop I had problem I never saw before, without any reason...

There are many things : 

- the mouse cursor is normal inside the windows, but it is a black cross outside the windows (?!)

- the windows don't have any border (that is : the windows start with the file menu etc.) 

- when 2 windows are bunked, I can make one to go at first plan (behind the second) by clicking on it, this doesn't do anything

-  windows doesn't appear in the task bar 

- screenlets doesn't work anymore

- virtual destkop doesn't work anymore

... All those things appeared this morning, without any reason ! I didn't chang my graphical drivers, I didn't install anything yesterday etc.


Any help ?...

Thanks !

---

### Post by dino99 on 2010-10-11
you might have usefull errors logged to help you (xsession-errors & xorg.0.log)

---

### Post by nandayo on 2010-10-11
thanks for your fast answer !

Well, not so usefull for me because I don't really understand all, but here are the content of those file :

.xsession-errors : 
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
/tmp/thunderbird.tbindicator.Default-fifo512
```

xorg.O.log:
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux emmanuel-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=3b886e6a-b974-4b7a-9e1b-c5acbe0918f3 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 11 12:01:52 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2a42:1028:0233 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf6c00000/4194304, 0xe0000000/268435456, I/O @ 0x0000ef98/8
(--) PCI: (0:0:2:1) 8086:2a43:1028:0233 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf6b00000/1048576
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
(--) intel(0): Chipset: "GM45"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): Output HDMI2 has no monitor section
(II) intel(0): Output DP2 has no monitor section
(II) intel(0): Output DP3 has no monitor section
(II) intel(0): Output TV1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 5442  Serial#: 0
(II) intel(0): Year: 2008  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 107.8 MHz   Image Size:  303 x 190 mm
(II) intel(0): h_active: 1440  h_sync: 1486  h_sync_end 1556 h_blank_end 1928 h_border: 0
(II) intel(0): v_active: 900  v_sync: 909  v_sync_end 918 v_blanking: 932 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.9 MHz   Image Size:  303 x 190 mm
(II) intel(0): h_active: 1440  h_sync: 1486  h_sync_end 1556 h_blank_end 1928 h_border: 0
(II) intel(0): v_active: 900  v_sync: 909  v_sync_end 918 v_blanking: 932 v_border: 0
(II) intel(0):  TT219141BT
(II) intel(0): Unknown vendor-specific block 0
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff004ca3425400000000
(II) intel(0):     00120103901e13780a87f594574f8c27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     0101010101011d2aa0e8518420302e46
(II) intel(0):     99002fbe1000001a141ca0e851842030
(II) intel(0):     2e4699002fbe1000001a000000fe0054
(II) intel(0):     543231398131343142540a2000000000
(II) intel(0):     000c10171b3669a9ff02010a202000d0
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1440x900"x60.0  107.81  1440 1486 1556 1928  900 909 918 932 +hsync -vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x40.0   71.88  1440 1486 1556 1928  900 909 918 932 +hsync -vsync (37.3 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP1
(II) intel(0): EDID for output HDMI2
(II) intel(0): EDID for output DP2
(II) intel(0): EDID for output DP3
(II) intel(0): EDID for output TV1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Output HDMI2 disconnected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Output DP3 disconnected
(II) intel(0): Output TV1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1440x900
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Kernel mode setting active, disabling FBC.
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 381 x 238
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event10)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event10"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "fr"
(**) Option "xkb_variant" "oss"
(II) XKB: reuse xkmfile /var/lib/xkb/server-03B9BA61C8A1BA78B8E8368594E484A532C88FC7.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event11)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event11"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "fr"
(**) Option "xkb_variant" "oss"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "fr"
(**) Option "xkb_variant" "oss"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "fr"
(**) Option "xkb_variant" "oss"
(II) config/udev: Adding input device HID 413c:8157 (/dev/input/event6)
(**) HID 413c:8157: Applying InputClass "evdev keyboard catchall"
(**) HID 413c:8157: always reports core events
(**) HID 413c:8157: Device: "/dev/input/event6"
(II) HID 413c:8157: Found keys
(II) HID 413c:8157: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 413c:8157" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "fr"
(**) Option "xkb_variant" "oss"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Sep Left Jack (/dev/input/event13)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Right Jack (/dev/input/event14)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Line Out at Sep Left Jack (/dev/input/event15)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Right Jack (/dev/input/event16)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device USB Optical Mouse (/dev/input/event5)
(**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) USB Optical Mouse: always reports core events
(**) USB Optical Mouse: Device: "/dev/input/event5"
(II) USB Optical Mouse: Found 3 mouse buttons
(II) USB Optical Mouse: Found scroll wheel(s)
(II) USB Optical Mouse: Found relative axes
(II) USB Optical Mouse: Found x and y relative axes
(II) USB Optical Mouse: Configuring as mouse
(**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
(II) USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "fr"
(**) Option "xkb_variant" "oss"
(II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event9)
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event9"
(II) AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767
(II) AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
(II) AlpsPS/2 ALPS DualPoint TouchPad: finger width range 0 - 0
(II) AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
(--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
(**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device DualPoint Stick (/dev/input/event7)
(**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
(**) DualPoint Stick: always reports core events
(**) DualPoint Stick: Device: "/dev/input/event7"
(II) DualPoint Stick: Found 3 mouse buttons
(II) DualPoint Stick: Found relative axes
(II) DualPoint Stick: Found x and y relative axes
(II) DualPoint Stick: Configuring as mouse
(**) DualPoint Stick: YAxisMapping: buttons 4 and 5
(**) DualPoint Stick: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE)
(II) DualPoint Stick: initialized for relative axes.
(II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
(**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event8"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "fr"
(**) Option "xkb_variant" "oss"
(II) intel(0): EDID vendor "SEC", prod id 21570
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.81  1440 1486 1556 1928  900 909 918 932 +hsync -vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x0.0   71.88  1440 1486 1556 1928  900 909 918 932 +hsync -vsync (37.3 kHz)
(II) intel(0): EDID vendor "SEC", prod id 21570
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.81  1440 1486 1556 1928  900 909 918 932 +hsync -vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x0.0   71.88  1440 1486 1556 1928  900 909 918 932 +hsync -vsync (37.3 kHz)
(II) intel(0): EDID vendor "SEC", prod id 21570
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.81  1440 1486 1556 1928  900 909 918 932 +hsync -vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x0.0   71.88  1440 1486 1556 1928  900 909 918 932 +hsync -vsync (37.3 kHz)
(II) intel(0): EDID vendor "SEC", prod id 21570
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.81  1440 1486 1556 1928  900 909 918 932 +hsync -vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x0.0   71.88  1440 1486 1556 1928  900 909 918 932 +hsync -vsync (37.3 kHz)
```

---

### Post by nandayo on 2010-10-11
I stopped all screenlets and restarted : same thing, with this xsession-errors log :
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=fr_FR.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[1813]: EggSMClient-WARNING: Desktop file '/home/emmanuel/.config/autostart/skype-1.desktop' has malformed Icon key 'skype.png'(should not include extension)
GNOME_KEYRING_CONTROL=/tmp/keyring-xZ8LBB
GNOME_KEYRING_PID=1859
GNOME_KEYRING_CONTROL=/tmp/keyring-xZ8LBB
GNOME_KEYRING_CONTROL=/tmp/keyring-xZ8LBB
SSH_AUTH_SOCK=/tmp/keyring-xZ8LBB/ssh
gnome-session[1813]: WARNING: Could not launch application 'ubuntuone-client-applet.desktop': Unable to start application: L'exécution du processus fils « ubuntuone-client-applet » a échoué (Aucun fichier ou dossier de ce type)
gnome-session[1813]: WARNING: Could not launch application 'lanuchy.desktop': Unable to start application: L'exécution du processus fils « lanuchy » a échoué (Aucun fichier ou dossier de ce type)

(polkit-gnome-authentication-agent-1:1909): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1909): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (nm-applet:1892): DEBUG: old state indicates that this was not a disconnect 0
** Message: adding killswitch idx 1 state 1
** Message: killswitch 1 is 1
** Message: killswitches state 1
** Message: killswitch 1 is 1
** Message: killswitches state 1
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension
** Message: Initializing gksu extension...
** (nm-applet:1892): DEBUG: foo_client_state_changed_cb

** (nautilus:1884): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:1884): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:1884): WARNING **: Can not get _NET_WORKAREA

** (nautilus:1884): WARNING **: Can not determine workarea, guessing at layout

(gnome-power-manager:1888): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x8392c0'

(gnome-settings-daemon:1861): GLib-GObject-WARNING **: IA__g_object_notify: object class `GkbdStatus' has no property named `name'
** (nm-applet:1892): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 41482 1286834400 1286792918
evolution-alarm-notify-Message:  Tue Oct 12 00:00:00 2010

evolution-alarm-notify-Message:  Mon Oct 11 12:28:38 2010

evolution-alarm-notify-Message: Setting timeout for 28881 1286821800 1286792919
evolution-alarm-notify-Message:  Mon Oct 11 20:30:00 2010

evolution-alarm-notify-Message:  Mon Oct 11 12:28:39 2010

evolution-alarm-notify-Message: Setting timeout for 28881 1286821800 1286792919
evolution-alarm-notify-Message:  Mon Oct 11 20:30:00 2010

evolution-alarm-notify-Message:  Mon Oct 11 12:28:39 2010

/tmp/thunderbird.tbindicator.Default-fifo204
** (update-notifier:2304): DEBUG: Skipping reboot required

(nautilus:1884): Nautilus-GDU-WARNING **: unable to query info: L'emplacement indiqué n'est pas pris en charge

```

Seems that many graphical things cannot be launched (screenlets, desktops etc.), don't know why this happens :-/

---

### Post by dino99 on 2010-10-11
i feel Lucid is lost with all your oldish tweaks :confused:

first make room and check your repo: you might have only genuine Lucid repo enabled into "synaptic repo tab"

remove all the  installed applets
remove xorg.conf: sudo rm -f /etc/X11/xorg.conf

check that xserver-xorg-video-intel is installed and activated (system admin additional driver)

sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure gnome-panel

reinstall the applets you need/want, then reboot

---

### Post by nandayo on 2010-10-11
As I said, I'm still under lucid, I didn't make any update yesterday... I had those problems this morning without any reason...

---

### Post by dino99 on 2010-10-11
my bad, put Lucid instead maverick in my post, you can follow it anyway (too many tweaks can kill your system)

---

### Post by nandayo on 2010-10-11
I followed your instructions : no change. By the way, I do not have any /etc/X11/xorg.conf ! I don't have many applets I think, actually I just have few screenlets...

However, it seems that I "fixed" the problem by just activating the visual effects in the "Appearance" menu... what the hell ? :confused:

---

### Post by nandayo on 2010-10-11
Damned, no, I didn't fix anything, the problem happens again each time I restart the session :-/

---

### Post by nandayo on 2010-10-11
Up...

---

### Post by nandayo on 2010-10-12
up... still have this boring problem :-/

---

