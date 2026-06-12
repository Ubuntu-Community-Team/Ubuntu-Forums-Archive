---
title: "uninstalling gtk-qt-engine"
date: 2010-11-26
forum: General Help
---

### Post by redlinethecar on 2010-11-26
For some reason when trying to remove qtk-qt-engine I get an error message like....

```
sean@Port-nix-system:~$ sudo apt-get remove gtk-qt-engine
[sudo] password for sean: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'gtk-qt-engine' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```

Now the reason I'm trying to remove this is because I get errors when installing and customizing a new theme I've downloaded. The shell script accesses gnome-appearence-properties with multiple errors. I've even tried to access it myself as root but still recieve errors. Here's what comes up.

BTW.. I'm running ubuntu 10.10 kernel 2.6.35-22-generic

```
root@Port-nix-system:~/Desktop_Themes/divergence_iv_____a_new_hope___by_jurialmunkey-d316eqx# ./install.sh
A-New-Hope/
A-New-Hope/metacity-1/
A-New-Hope/gtk-2.0/
A-New-Hope/gtk-2.0/Styles/
A-New-Hope/gtk-2.0/Toolbar/
A-New-Hope/gtk-2.0/Breadcrumbs/
A-New-Hope/gtk-2.0/Styles/RES/
A-New-Hope/gtk-2.0/Breadcrumbs/Dust/
A-New-Hope/gtk-2.0/Breadcrumbs/Metal/
A-New-Hope/gtk-2.0/Breadcrumbs/Light/
A-New-Hope/tabs-default.png
A-New-Hope/tabs-dark.png
A-New-Hope/scrollbar-light.png
A-New-Hope/scrollbar-dark.png
A-New-Hope/panel-sunken.png
A-New-Hope/panel-raised.png
A-New-Hope/panel-light.png
A-New-Hope/nautilus-TESB.png
A-New-Hope/nautilus-ROTJ.png
A-New-Hope/nautilus-default.png
A-New-Hope/menu-sunken.png
A-New-Hope/menu-raised.png
A-New-Hope/menu-lessrounded.png
A-New-Hope/main.png
A-New-Hope/azel-icon.png
A-New-Hope/index.theme
A-New-Hope/metacity-1/metacity-theme-1.xml
A-New-Hope/metacity-1/button-close-pressed.png
A-New-Hope/metacity-1/title-right.png
A-New-Hope/metacity-1/title.png
A-New-Hope/metacity-1/top_right-4.png
A-New-Hope/metacity-1/top_left-2.png
A-New-Hope/metacity-1/button-close-unfocused.png
A-New-Hope/metacity-1/button-menu-normal.png
A-New-Hope/metacity-1/button-minimize-unfocused.png
A-New-Hope/metacity-1/top_left.png
A-New-Hope/metacity-1/button-maximize-unfocused.png
A-New-Hope/metacity-1/button-maximize-normal.png
A-New-Hope/metacity-1/button-fill.png
A-New-Hope/metacity-1/button-minimize-focused.png
A-New-Hope/metacity-1/button-minimize.png
A-New-Hope/metacity-1/button-menu-unfocused.png
A-New-Hope/metacity-1/button-close-normal.png
A-New-Hope/metacity-1/button-menu-focused.png
A-New-Hope/metacity-1/button-close-focused.png
A-New-Hope/metacity-1/button-inactive.png
A-New-Hope/metacity-1/button-minimize-normal.png
A-New-Hope/metacity-1/button-maximize-pressed.png
A-New-Hope/metacity-1/button-maximize-focused.png
A-New-Hope/metacity-1/top_right.png
A-New-Hope/metacity-1/button-minimize-pressed.png
A-New-Hope/metacity-1/button-menu-pressed.png
A-New-Hope/gtk-2.0/gtkrc
A-New-Hope/gtk-2.0/Styles/toolbar.rc
A-New-Hope/gtk-2.0/Styles/scrollbar.rc
A-New-Hope/gtk-2.0/Styles/panel.rc
A-New-Hope/gtk-2.0/Styles/notebook.rc
A-New-Hope/gtk-2.0/Styles/nautilus.rc
A-New-Hope/gtk-2.0/Styles/menu.rc
A-New-Hope/gtk-2.0/Styles/button.rc
A-New-Hope/gtk-2.0/Styles/breadcrumbs.rc
A-New-Hope/gtk-2.0/Toolbar/oldpanel.png
A-New-Hope/gtk-2.0/Toolbar/toolbar.png
A-New-Hope/gtk-2.0/Toolbar/panel.png
A-New-Hope/gtk-2.0/Toolbar/handle.png
A-New-Hope/gtk-2.0/Toolbar/toolbar-old.png
A-New-Hope/gtk-2.0/Toolbar/extra-widget.png
A-New-Hope/gtk-2.0/Toolbar/handleb.png
A-New-Hope/gtk-2.0/Breadcrumbs/right_slider.png
A-New-Hope/gtk-2.0/Breadcrumbs/prelight.png
A-New-Hope/gtk-2.0/Breadcrumbs/normal.png
A-New-Hope/gtk-2.0/Breadcrumbs/left_slider.png
A-New-Hope/gtk-2.0/Breadcrumbs/active.png
A-New-Hope/gtk-2.0/Styles/RES/menu-square.rc
A-New-Hope/gtk-2.0/Styles/RES/menu-lessround.rc
A-New-Hope/gtk-2.0/Styles/RES/panel-raised.rc
A-New-Hope/gtk-2.0/Styles/RES/nautilus-ROTJ.rc
A-New-Hope/gtk-2.0/Styles/RES/null.rc
A-New-Hope/gtk-2.0/Styles/RES/panel-light.rc
A-New-Hope/gtk-2.0/Styles/RES/nautilus-TESB.rc
A-New-Hope/gtk-2.0/Styles/RES/breadcrumbs-light.rc
A-New-Hope/gtk-2.0/Styles/RES/toolbar-light.rc
A-New-Hope/gtk-2.0/Styles/RES/toolbar-dark.rc
A-New-Hope/gtk-2.0/Styles/RES/scrollbar-dark.rc
A-New-Hope/gtk-2.0/Styles/RES/scrollbar-light.rc
A-New-Hope/gtk-2.0/Styles/RES/panel-sunken.rc
A-New-Hope/gtk-2.0/Styles/RES/notebook-dark.rc
A-New-Hope/gtk-2.0/Styles/RES/notebook-light.rc
A-New-Hope/gtk-2.0/Styles/RES/nautilus-ANH.rc
A-New-Hope/gtk-2.0/Styles/RES/menu-round.rc
A-New-Hope/gtk-2.0/Styles/RES/button-light.rc
A-New-Hope/gtk-2.0/Styles/RES/breadcrumbs-dark.rc
A-New-Hope/gtk-2.0/Styles/RES/menu-raised.rc
A-New-Hope/gtk-2.0/Breadcrumbs/Dust/right_slider.png
A-New-Hope/gtk-2.0/Breadcrumbs/Dust/prelight.png
A-New-Hope/gtk-2.0/Breadcrumbs/Dust/normal.png
A-New-Hope/gtk-2.0/Breadcrumbs/Dust/left_slider.png
A-New-Hope/gtk-2.0/Breadcrumbs/Dust/active.png
A-New-Hope/gtk-2.0/Breadcrumbs/Metal/right_slider.png
A-New-Hope/gtk-2.0/Breadcrumbs/Metal/prelight.png
A-New-Hope/gtk-2.0/Breadcrumbs/Metal/normal.png
A-New-Hope/gtk-2.0/Breadcrumbs/Metal/left_slider.png
A-New-Hope/gtk-2.0/Breadcrumbs/Metal/active.png
A-New-Hope/gtk-2.0/Breadcrumbs/Light/prelight.png
A-New-Hope/gtk-2.0/Breadcrumbs/Light/normal.png
A-New-Hope/gtk-2.0/Breadcrumbs/Light/left_slider.png
A-New-Hope/gtk-2.0/Breadcrumbs/Light/active.png
A-New-Hope/gtk-2.0/Breadcrumbs/Light/right_slider.png
A-New-Hope/customise.py
A-New-Hope/ANewHopeConfigurator.ui
gnome-appearance-properties: no process found

(gnome-appearance-properties:3190): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:3190): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
root@Port-nix-system:~/Desktop_Themes/divergence_iv_____a_new_hope___by_jurialmunkey-d316eqx# gnome-appearance-properties

(gnome-appearance-properties:3195): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:3195): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
root@Port-nix-system:~/Desktop_Themes/divergence_iv_____a_new_hope___by_jurialmunkey-d316eqx# 

```

Can't figure this one out for the life of me.

---

