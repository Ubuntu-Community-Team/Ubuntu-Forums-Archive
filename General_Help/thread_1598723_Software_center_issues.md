---
title: "Software center issues"
date: 2010-10-16
forum: General Help
---

### Post by palz2015 on 2010-10-16
I updated to 10.10 today. It just updated via a normal update, not a distribution update. When I rebooted, software center simply doesn't launch. I was installing adobe air from a deb, and it opened with archive manager, not SC, like it should in 10.10. I can't even get it to open with gdebi (don't know how).

From terminal, it says:
```
mistic@mistic-laptop:/usr/bin$ ./software-center
/usr/share/software-center/softwarecenter/view/softwarepane.py:90: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  self.app_view = AppView(show_ratings)
/usr/share/software-center/softwarecenter/view/softwarepane.py:90: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  self.app_view = AppView(show_ratings)
/usr/share/software-center/softwarecenter/view/softwarepane.py:90: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  self.app_view = AppView(show_ratings)
/usr/share/software-center/softwarecenter/view/softwarepane.py:90: Warning: g_object_remove_toggle_ref: assertion `G_IS_OBJECT (object)' failed
  self.app_view = AppView(show_ratings)
/usr/share/software-center/softwarecenter/view/availablepane.py:117: GtkWarning: IA__gtk_widget_set_state: assertion `GTK_IS_WIDGET (widget)' failed
  self.notebook.append_page(self.apps_vbox, gtk.Label("installed"))
/usr/share/software-center/softwarecenter/view/availablepane.py:119: GtkWarning: IA__gtk_widget_set_state: assertion `GTK_IS_WIDGET (widget)' failed
  self.notebook.append_page(self.scroll_details, gtk.Label(self.NAV_BUTTON_ID_DETAILS))
/usr/share/software-center/softwarecenter/view/availablepane.py:79: Warning: g_object_ref: assertion `G_IS_OBJECT (object)' failed
  self._build_ui()
/usr/share/software-center/softwarecenter/view/availablepane.py:79: Warning: instance of invalid non-instantiatable type `<invalid>'
  self._build_ui()
/usr/share/software-center/softwarecenter/view/availablepane.py:79: Warning: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self._build_ui()
/usr/share/software-center/softwarecenter/view/availablepane.py:79: GtkWarning: IA__gtk_widget_set_state: assertion `GTK_IS_WIDGET (widget)' failed
  self._build_ui()
/usr/share/software-center/softwarecenter/view/availablepane.py:79: GtkWarning: IA__gtk_widget_unparent: assertion `GTK_IS_WIDGET (widget)' failed
  self._build_ui()
/usr/share/software-center/softwarecenter/view/availablepane.py:79: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  self._build_ui()
/usr/share/software-center/softwarecenter/view/availablepane.py:79: GtkWarning: IA__gtk_widget_get_realized: assertion `GTK_IS_WIDGET (widget)' failed
  self._build_ui()
/usr/share/software-center/softwarecenter/view/availablepane.py:79: Warning: instance with invalid (NULL) class pointer
  self._build_ui()
/usr/share/software-center/softwarecenter/view/availablepane.py:79: Warning: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self._build_ui()
/usr/share/software-center/softwarecenter/view/availablepane.py:79: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self._build_ui()
/usr/share/software-center/softwarecenter/app.py:166: GtkWarning: IA__gtk_widget_has_rc_style: assertion `GTK_IS_WIDGET (widget)' failed
  self.alignment_available.add(self.available_pane)
/usr/share/software-center/softwarecenter/app.py:166: GtkWarning: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
  self.alignment_available.add(self.available_pane)
Segmentation fault

```

This doesn't happen on any other ubuntu machine I have.

---

### Post by palz2015 on 2010-10-19
Please help, bump

---

### Post by palz2015 on 2010-10-19
This is what I get when I try to reinstall it:
```

mistic@mistic-laptop:~$ sudo apt-get clean
[sudo] password for mistic: 
mistic@mistic-laptop:~$ sudo apt-get install --reinstall software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apt apt-transport-https apt-utils aptdaemon aptitude
  libboost-iostreams1.42.0 libept1 python-apt python-aptdaemon
  python-aptdaemon-gtk sessioninstaller synaptic
Suggested packages:
  apt-doc aptitude-doc-en aptitude-doc debtags python-apt-dbg python-apt-doc
  dwww deborphan
Recommended packages:
  gpg
The following packages will be REMOVED:
  libept0
The following NEW packages will be installed:
  libboost-iostreams1.42.0 libept1 sessioninstaller
The following packages will be upgraded:
  apt apt-transport-https apt-utils aptdaemon aptitude python-apt
  python-aptdaemon python-aptdaemon-gtk software-center synaptic
10 upgraded, 3 newly installed, 1 to remove and 175 not upgraded.
Need to get 6,709kB of archives.
After this operation, 8,110kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main python-apt 0.7.96.1ubuntu11 [200kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/main libept1 1.0.3 [145kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ maverick/main synaptic 0.63.1ubuntu14 [850kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ maverick/main apt-utils 0.8.3ubuntu7 [269kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ maverick/main apt-transport-https 0.8.3ubuntu7 [92.3kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ maverick/main libboost-iostreams1.42.0 1.42.0-3ubuntu1 [58.9kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ maverick/main aptitude 0.6.3-2ubuntu4 [2,270kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ maverick/main apt 0.8.3ubuntu7 [2,076kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ maverick/main python-aptdaemon-gtk 0.31+bzr506-0ubuntu2 [197kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ maverick/main aptdaemon 0.31+bzr506-0ubuntu2 [23.2kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ maverick/main python-aptdaemon 0.31+bzr506-0ubuntu2 [63.9kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ maverick/main software-center 3.0.4 [435kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ maverick/main sessioninstaller 0.20+bzr115-0ubuntu1 [28.2kB]
Fetched 6,709kB in 4s (1,446kB/s)     
(Reading database ... 173757 files and directories currently installed.)
Preparing to replace python-apt 0.7.94.2ubuntu6.2 (using .../python-apt_0.7.96.1ubuntu11_i386.deb) ...
Unpacking replacement python-apt ...
Selecting previously deselected package libept1.
Unpacking libept1 (from .../libept1_1.0.3_i386.deb) ...
Preparing to replace synaptic 0.63.1ubuntu7 (using .../synaptic_0.63.1ubuntu14_i386.deb) ...
Unpacking replacement synaptic ...
Preparing to replace apt-utils 0.7.25.3ubuntu9.1 (using .../apt-utils_0.8.3ubuntu7_i386.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace apt-transport-https 0.7.25.3ubuntu9.1 (using .../apt-transport-https_0.8.3ubuntu7_i386.deb) ...
Unpacking replacement apt-transport-https ...
Selecting previously deselected package libboost-iostreams1.42.0.
Unpacking libboost-iostreams1.42.0 (from .../libboost-iostreams1.42.0_1.42.0-3ubuntu1_i386.deb) ...
Preparing to replace aptitude 0.4.11.11-1ubuntu10 (using .../aptitude_0.6.3-2ubuntu4_i386.deb) ...
Unpacking replacement aptitude ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for python-support ...
(Reading database ... 173780 files and directories currently installed.)
Removing libept0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 173774 files and directories currently installed.)
Preparing to replace apt 0.7.25.3ubuntu9.1 (using .../apt_0.8.3ubuntu7_i386.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.3ubuntu7) ...
Installing new version of config file /etc/apt/apt.conf.d/01autoremove ...
Installing new version of config file /etc/cron.daily/apt ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 173793 files and directories currently installed.)
Preparing to replace python-aptdaemon-gtk 0.11+bzr345-0ubuntu4.1 (using .../python-aptdaemon-gtk_0.31+bzr506-0ubuntu2_all.deb) ...
Unpacking replacement python-aptdaemon-gtk ...
Preparing to replace aptdaemon 0.11+bzr345-0ubuntu4.1 (using .../aptdaemon_0.31+bzr506-0ubuntu2_all.deb) ...
Unpacking replacement aptdaemon ...
Preparing to replace python-aptdaemon 0.11+bzr345-0ubuntu4.1 (using .../python-aptdaemon_0.31+bzr506-0ubuntu2_all.deb) ...
Unpacking replacement python-aptdaemon ...
Preparing to replace software-center 2.0.7 (using .../software-center_3.0.4_all.deb) ...
Unpacking replacement software-center ...
Selecting previously deselected package sessioninstaller.
Unpacking sessioninstaller (from .../sessioninstaller_0.20+bzr115-0ubuntu1_all.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for gconf2 ...
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Processing triggers for python-support ...
Setting up apt-utils (0.8.3ubuntu7) ...
Setting up python-apt (0.7.96.1ubuntu11) ...
Setting up libept1 (1.0.3) ...
Setting up synaptic (0.63.1ubuntu14) ...
Setting up apt-transport-https (0.8.3ubuntu7) ...
Setting up libboost-iostreams1.42.0 (1.42.0-3ubuntu1) ...
Setting up aptitude (0.6.3-2ubuntu4) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Processing triggers for python-central ...
Setting up python-aptdaemon (0.31+bzr506-0ubuntu2) ...
Processing triggers for python-central ...
Setting up python-aptdaemon-gtk (0.31+bzr506-0ubuntu2) ...
Setting up aptdaemon (0.31+bzr506-0ubuntu2) ...
Processing triggers for python-central ...
Setting up software-center (3.0.4) ...
Setting up sessioninstaller (0.20+bzr115-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Processing triggers for python-central ...
Processing triggers for python-support ...
mistic@mistic-laptop:~$ 

```

And when I try to run it:
```

mistic@mistic-laptop:/usr/bin$ ./software-center/usr/share/software-center/softwarecenter/view/widgets/mkit.py:140: Warning: instance with invalid (NULL) class pointer
  EM = get_em_value()
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:140: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  EM = get_em_value()
2010-10-19 11:49:14,940 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 96, 'open')'
2010-10-19 11:49:14,939 - root - WARNING - failed to add sca db Couldn't detect type of database
/usr/share/software-center/softwarecenter/view/appview.py:1192: Warning: instance of invalid non-instantiatable type `<invalid>'
  tr.set_button_spacing(int(get_em_value()*0.3+0.5))
/usr/share/software-center/softwarecenter/view/appview.py:1192: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  tr.set_button_spacing(int(get_em_value()*0.3+0.5))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1250: GtkWarning: IA__gtk_widget_get_realized: assertion `GTK_IS_WIDGET (widget)' failed
  self.screenshot = ScreenshotView(self.distro, self.icons)
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1250: Warning: instance of invalid non-instantiatable type `<invalid>'
  self.screenshot = ScreenshotView(self.distro, self.icons)
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1250: Warning: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.screenshot = ScreenshotView(self.distro, self.icons)
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1250: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.screenshot = ScreenshotView(self.distro, self.icons)
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1254: GtkWarning: IA__gtk_widget_get_realized: assertion `GTK_IS_WIDGET (widget)' failed
  self.homepage_btn = mkit.HLinkButton(_('Website'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1254: Warning: instance with invalid (NULL) class pointer
  self.homepage_btn = mkit.HLinkButton(_('Website'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1254: Warning: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.homepage_btn = mkit.HLinkButton(_('Website'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1254: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.homepage_btn = mkit.HLinkButton(_('Website'))
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:1100: Warning: invalid uninstantiatable type `(null)' in cast to `GtkLabel'
  self.label.set_markup('<u>%s</u>' % self.label.get_text())
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:1100: GtkWarning: IA__gtk_label_get_text: assertion `GTK_IS_LABEL (label)' failed
  self.label.set_markup('<u>%s</u>' % self.label.get_text())
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:1100: GtkWarning: IA__gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed
  self.label.set_markup('<u>%s</u>' % self.label.get_text())
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1261: GtkWarning: IA__gtk_widget_get_realized: assertion `GTK_IS_WIDGET (widget)' failed
  self.share_btn = mkit.HLinkButton(_('Share...'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1261: Warning: instance of invalid non-instantiatable type `<invalid>'
  self.share_btn = mkit.HLinkButton(_('Share...'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1261: Warning: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.share_btn = mkit.HLinkButton(_('Share...'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1261: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.share_btn = mkit.HLinkButton(_('Share...'))
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:1100: Warning: invalid uninstantiatable type `<invalid>' in cast to `GtkLabel'
  self.label.set_markup('<u>%s</u>' % self.label.get_text())
Segmentation fault


```

---

### Post by palz2015 on 2010-10-28
I tried apt-get update and  sudo aptitude reinstall software-center and even sudo rm /etc/apt/*bin with no success. 
When I run aptitude upgrade (doesn't help, but installs new software-center package) I get a weird thing:
```

WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Setting up libgconf2-dev (2.31.91-0ubuntu3.1) 

```

And again here's the output:
```


mistic@mistic-laptop:~$ software-center
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:140: Warning: instance with invalid (NULL) class pointer
  EM = get_em_value()
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:140: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  EM = get_em_value()
2010-10-28 19:24:23,351 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 96, 'open')'
2010-10-28 19:24:23,351 - root - WARNING - failed to add sca db Couldn't detect type of database
/usr/share/software-center/softwarecenter/view/appview.py:1196: Warning: instance of invalid non-instantiatable type `<invalid>'
  tr.set_button_spacing(int(get_em_value()*0.3+0.5))
/usr/share/software-center/softwarecenter/view/appview.py:1196: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  tr.set_button_spacing(int(get_em_value()*0.3+0.5))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1250: GtkWarning: IA__gtk_widget_get_realized: assertion `GTK_IS_WIDGET (widget)' failed
  self.screenshot = ScreenshotView(self.distro, self.icons)
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1250: Warning: instance of invalid non-instantiatable type `<invalid>'
  self.screenshot = ScreenshotView(self.distro, self.icons)
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1250: Warning: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.screenshot = ScreenshotView(self.distro, self.icons)
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1250: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.screenshot = ScreenshotView(self.distro, self.icons)
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1254: GtkWarning: IA__gtk_widget_get_realized: assertion `GTK_IS_WIDGET (widget)' failed
  self.homepage_btn = mkit.HLinkButton(_('Website'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1254: Warning: instance with invalid (NULL) class pointer
  self.homepage_btn = mkit.HLinkButton(_('Website'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1254: Warning: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.homepage_btn = mkit.HLinkButton(_('Website'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1254: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.homepage_btn = mkit.HLinkButton(_('Website'))
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:1100: Warning: invalid uninstantiatable type `(null)' in cast to `GtkLabel'
  self.label.set_markup('<u>%s</u>' % self.label.get_text())
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:1100: GtkWarning: IA__gtk_label_get_text: assertion `GTK_IS_LABEL (label)' failed
  self.label.set_markup('<u>%s</u>' % self.label.get_text())
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:1100: GtkWarning: IA__gtk_label_set_markup: assertion `GTK_IS_LABEL (label)' failed
  self.label.set_markup('<u>%s</u>' % self.label.get_text())
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1261: GtkWarning: IA__gtk_widget_get_realized: assertion `GTK_IS_WIDGET (widget)' failed
  self.share_btn = mkit.HLinkButton(_('Share...'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1261: Warning: instance of invalid non-instantiatable type `<invalid>'
  self.share_btn = mkit.HLinkButton(_('Share...'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1261: Warning: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.share_btn = mkit.HLinkButton(_('Share...'))
/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py:1261: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.share_btn = mkit.HLinkButton(_('Share...'))
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:1100: Warning: invalid uninstantiatable type `<invalid>' in cast to `GtkLabel'
  self.label.set_markup('<u>%s</u>' % self.label.get_text())
Segmentation fault

```
This is really annoying me, please help

---

### Post by palz2015 on 2010-10-29
Sorry for the bumping, but can you atleast point me in the right direction?

---

### Post by palz2015 on 2010-11-05
Help please

---

### Post by sameer.abuasal on 2010-12-22
I am facing the same problem here. 

I just updated to 10.10 and software center is not running, showing the same error. also gedit is not working, I believe it has something to doo with a GTK Lib file or something !!!


Did you ever find a solution for this ?

---

### Post by sameer.abuasal on 2010-12-22
I took a second look at the error log I found it had something to do with the python GTK libraries, I installed python-gtk2 and everything was solved.
you might want to try it.

---

