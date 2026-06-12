---
title: "XUbuntu 12.04 Display Freeze"
date: 2012-06-20
forum: General Help
---

### Post by sgharp on 2012-06-20
Hi Guys,

I've just upgraded to Xubuntu 12.04 x64 from 11.10 and I'm the display freezes before it even finishes painting.

Symtoms:
Display frozen
Mouse cursor moves fine but doesn't affect anything.
I can ssh into the machine and have no problems with a remote terminal interface.
I cannot Ctrl+Alt+F1 to get a level 3 login.

Display adapter : GeForce 7300 GS

I completed the upgrade and the system started freezing after a few minutes.  I installed the additional drivers recommended video driver and now it freezes before I even get a fully display UI.

The logs (see below) seem to indicate a problem with 3D which I didn't know xfce used.  Should I disable 3D and, if so, how do I do this from a terminal window (ssh)?

Here's some log data.
/var/log/Xorg.0.log  ~ this is repeated several hundred times
[   955.539] (EE) NVIDIA(0): Failed to allocate 3D objects
[   955.539] (EE) NVIDIA(0):  *** Aborting ***
[   955.539] (EE) NVIDIA(0): Error recovery failed.
[   955.539] (EE) NVIDIA(0):  *** Aborting ***

/var/log/lightdm/x-0-greeter.log
[+73.30s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+73.30s] DEBUG: count_batteries found 0 batteries (0 are charging/discharging)
[+73.30s] DEBUG: should_be_visible: no
[+73.30s] DEBUG: menubar.vala:519: Removing indicator object 0x19bb598
[+73.30s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+73.30s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+73.30s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+73.30s] WARNING: menubar.vala:531: Indicator object 0x19bb598 not in menubar
[+73.30s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu
[+73.30s] DEBUG: notify visible signal received
[+73.30s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+73.30s] DEBUG: notify visible signal received
[+73.30s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+73.31s] WARNING: Group Properties error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name :1.11 was not provided by any .service files
[+73.31s] DEBUG: Error getting properties on a new menuitem: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name :1.11 was not provided by any .service files
[+73.31s] DEBUG: Error getting properties on a new menuitem: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name :1.11 was not provided by any .service files
[+73.31s] DEBUG: Error getting properties on a new menuitem: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name :1.11 was not provided by any .service files
[+73.33s] DEBUG: unity-greeter.vala:310: starting system-ready sound
[+98.49s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+98.49s] CRITICAL: background_loader_create_pattern: assertion `image != NULL' failed
[+98.49s] DEBUG: Restarting service 'com.canonical.indicator.datetime' count 1
[+98.49s] DEBUG: Restarting service 'com.canonical.indicator.sound' count 1
[+98.52s] DEBUG: notify visible signal received
[+98.52s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+98.53s] DEBUG: New calendar item
[+99.30s] DEBUG: indicator-sound: new_volume_slider_widget
[+99.31s] DEBUG: indicator-sound: new_voip_slider_widget

/var/log/lightdm/x-0.log
(EE) NVIDIA(0): Failed to initialize the 3D engine
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Failed to allocate 3D objects
(EE) NVIDIA(0):  *** Aborting ***

Thanks for any help...

---

