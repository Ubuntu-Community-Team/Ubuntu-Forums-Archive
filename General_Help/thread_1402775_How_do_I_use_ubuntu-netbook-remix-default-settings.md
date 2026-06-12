---
title: "How do I use ubuntu-netbook-remix-default-settings?"
date: 2010-02-09
forum: General Help
---

### Post by CoreyB. on 2010-02-09
The package "ubuntu-netbook-remix-default-settings" installs a file "/usr/share/gconf/defaults/30_ubuntu-netbook-remix-default-settings".  What is the proper way to enable these settings and fall back to these defaults?

---

### Post by mikewhatever on 2010-02-09
Not sure what you mean by 'proper way', but creating a new user might work.

---

### Post by CoreyB. on 2010-02-12
> **mikewhatever said:**
> Not sure what you mean by 'proper way', but creating a new user might work.

I mean like is there some graphical way or command line operation  to perform on the "/usr/share/gconf/defaults/30_ubuntu-netbook-remix-default-settings" file to make all of the settings apply to the current user?

---

### Post by CoreyB. on 2010-02-15
/usr/share/gconf/defaults/30_ubuntu-netbook-remix-default-settings

looks like this:

/desktop/gnome/applications/window_manager/default /usr/bin/metacity
/desktop/gnome/applications/window_manager/current /usr/bin/metacity
/apps/metacity/general/num_workspaces 1
/desktop/gnome/background/picture_options stretched
/desktop/gnome/interface/gtk_theme Dust
/desktop/gnome/interface/icon_theme Humanity-Dark
/desktop/gnome/lockdown/disable_user_switching true
/desktop/gnome/url-handlers/cdda/command rhythmbox %s
/apps/maximus/exclude_class [Empathy,Totem,Gwibber,Gnome-language-selector,Gtk-recordMyDesktop]
/apps/evolution/shell/view_defaults/buttons_style icons
/apps/evolution/shell/view_defaults/folder_bar/width 266
/apps/gnome-screensaver/user_switch_enabled false
/apps/nautilus/preferences/show_desktop false
/apps/nautilus/preferences/exit_with_last_window false
/apps/panel/general/toplevel_id_list [top_panel]
/apps/panel/general/applet_id_list [applet_0,applet_1,applet_2,applet_3,applet_4,applet_5,applet_6]
/apps/panel/general/toplevels/top_panel/background/color #000000
/apps/panel/general/toplevels/top_panel/background/opacity 37672
/apps/panel/general/toplevels/top_panel/background/type color
/apps/panel/applets/applet_0/bonobo_iid OAFIID:GNOME_GoHome
/apps/panel/applets/applet_0/locked true
/apps/panel/applets/applet_0/position 0
/apps/panel/applets/applet_0/object_type bonobo-applet
/apps/panel/applets/applet_0/toplevel_id top_panel
/apps/panel/applets/applet_1/bonobo_iid OAFIID:GNOME_WindowPicker
/apps/panel/applets/applet_1/locked true
/apps/panel/applets/applet_1/position 2
/apps/panel/applets/applet_1/object_type bonobo-applet
/apps/panel/applets/applet_1/toplevel_id top_panel
/apps/panel/applets/applet_2/bonobo_iid OAFIID:GNOME_IndicatorApplet
/apps/panel/applets/applet_2/locked true
/apps/panel/applets/applet_2/position 7
/apps/panel/applets/applet_2/object_type bonobo-applet
/apps/panel/applets/applet_2/panel_right_stick true
/apps/panel/applets/applet_2/toplevel_id top_panel
/apps/panel/applets/applet_3/bonobo_iid OAFIID:GNOME_NotificationAreaApplet
/apps/panel/applets/applet_3/locked true
/apps/panel/applets/applet_3/position 6
/apps/panel/applets/applet_3/object_type bonobo-applet
/apps/panel/applets/applet_3/panel_right_stick true
/apps/panel/applets/applet_3/toplevel_id top_panel
/apps/panel/applets/applet_4/bonobo_iid OAFIID:GNOME_MixerApplet
/apps/panel/applets/applet_4/locked true
/apps/panel/applets/applet_4/position 5
/apps/panel/applets/applet_4/object_type bonobo-applet
/apps/panel/applets/applet_4/panel_right_stick true
/apps/panel/applets/applet_4/toplevel_id top_panel
/apps/panel/applets/applet_5/bonobo_iid OAFIID:GNOME_ClockApplet
/apps/panel/applets/applet_5/locked true
/apps/panel/applets/applet_5/position 4
/apps/panel/applets/applet_5/object_type bonobo-applet
/apps/panel/applets/applet_5/panel_right_stick true
/apps/panel/applets/applet_5/toplevel_id top_panel
/apps/panel/applets/applet_6/bonobo_iid OAFIID:GNOME_FastUserSwitchApplet
/apps/panel/applets/applet_6/locked true
/apps/panel/applets/applet_6/position 3
/apps/panel/applets/applet_6/object_type bonobo-applet
/apps/panel/applets/applet_6/panel_right_stick true
/apps/panel/applets/applet_6/toplevel_id top_panel
/apps/panel/toplevels/disable_movement true
/apps/gnome-power-manager/buttons/lid_ac suspend
/apps/gnome-power-manager/buttons/lid_battery suspend
/apps/gnome-power-manager/buttons/power interactive
/apps/gnome-power-manager/buttons/suspend suspend
/apps/gnome-power-manager/actions/critical_battery suspend
/apps/gnome-power-manager/actions/sleep_type_ac suspend
/apps/gnome-power-manager/actions/sleep_type_battery suspend
/apps/gnome-power-manager/timeout/sleep_computer_ac 0
/apps/gnome-power-manager/timeout/sleep_display_ac 1200
/apps/gnome-power-manager/timeout/sleep_computer_battery 1200
/apps/gnome-power-manager/timeout/sleep_display_battery 300
/apps/gnome-power-manager/backlight/battery_reduce true
/apps/gnome-power-manager/ui/enable_sound false
/apps/gnome-power-manager/ui/icon_policy always
/apps/gnome-power-manager/lock/use_screensaver_settings true
/apps/gnome-power-manager/general/use_time_for_policy false
/apps/gnome-power-manager/notify/sleep_failed false
/apps/metacity/general/audible_bell false
/apps/f-spot/ui/maximized true
/apps/gnome-do/preferences/Do/CorePreferences/QuietStart true
/apps/netbook-launcher/favorites/favorites_list [firefox,evolution,cheese,empathy,yelp,ubuntuone-client-applet,ubuntu-software-center]
/apps/netbook-launcher/favorites/firefox/type application
/apps/netbook-launcher/favorites/firefox/desktop_file /usr/share/applications/firefox.desktop
/apps/netbook-launcher/favorites/evolution/type application
/apps/netbook-launcher/favorites/evolution/desktop_file /usr/share/applications/evolution.desktop
/apps/netbook-launcher/favorites/cheese/type application
/apps/netbook-launcher/favorites/cheese/desktop_file /usr/share/applications/cheese.desktop
/apps/netbook-launcher/favorites/empathy/type application
/apps/netbook-launcher/favorites/empathy/desktop_file /usr/share/applications/empathy.desktop
/apps/netbook-launcher/favorites/yelp/type application
/apps/netbook-launcher/favorites/yelp/desktop_file /usr/share/applications/yelp.desktop
/apps/netbook-launcher/favorites/ubuntuone-client-applet/type application
/apps/netbook-launcher/favorites/ubuntuone-client-applet/desktop_file /usr/share/applications/ubuntuone-client-applet.desktop
/apps/netbook-launcher/favorites/ubuntu-software-center/type application
/apps/netbook-launcher/favorites/ubuntu-software-center/desktop_file /usr/share/applications/ubuntu-software-center.desktop


How do I make these settings apply to the current user and all other users created from now on?

Thanks!

---

