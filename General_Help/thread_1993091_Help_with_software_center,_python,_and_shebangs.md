---
title: "Help with software center, python, and shebangs"
date: 2012-06-01
forum: General Help
---

### Post by theigmo87 on 2012-06-01
I have ubuntu 12.04, and I recently started having problems opening the software center, ubuntu one, as well as using some addons in xbmc. I think it began after I tried to start learning the python programming language. I didn't change any path variables that I know of, but for some reason I've been getting alot of errors dealing with python scripts. 

When I try to start software center from the gnome 3.4 dash, it crashes, and when I start it from the command line I get this message:


> software-center
2012-06-01 13:08:03,332 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-06-01 13:08:03,337 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True

(software-center:27824): Gtk-WARNING **: Theme directory apps/24 of theme fs-icons-gnome-style has no size field


(software-center:27824): Gtk-WARNING **: Theme directory status/24 of theme fs-icons-gnome-style has no size field


(software-center:27824): Gtk-WARNING **: Theme directory apps/24 of theme fs-icons has no size field


(software-center:27824): Gtk-WARNING **: Theme directory status/24 of theme fs-icons has no size field

2012-06-01 13:08:03,750 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-06-01 13:08:04,367 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1358, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1288, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 149, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 168, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 240, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 491, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 268, in _build_homepage_view
    self._append_recommended_for_you()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 461, in _append_recommended_for_you
    self.recommended_for_you_panel = RecommendationsPanelLobby(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/recommendations.py", line 169, in __init__
    self._try_sso_login()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/recommendations.py", line 233, in _try_sso_login
    self.RECOMMENDATIONS_OPT_IN_TEXT)
  File "/usr/share/software-center/softwarecenter/backend/login_sso.py", line 164, in get_sso_backend
    sso_class = LoginBackendDbusSSO(window_id, appname, help_text)
  File "/usr/share/software-center/softwarecenter/backend/login_sso.py", line 48, in __init__
    'com.ubuntu.sso', '/com/ubuntu/sso/credentials')
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1

So I've been looking around at bug reports the last few days and haven't found anything, and then I found one page where someone had trouble with scripts that began with the shebang !#/usr/bin/env python. I changed the shebang in /usr/lib/ubuntu-sso-client/ubuntu-sso-login to !#/usr/bin/python and magically the ubuntu software center opens with no problems! and ubuntu one opens from the dash as well, but now has problems with credentials which I can figure out later. I couldn't get u1sdtool to work at the beginning, but changing the shebang in that worked as well. I have no clue what's going on, but can someone tell me why the modified shebang would work and the original using env python wouldn't? I am pretty familiar with linux but not an expert by any means. I'm think the env python deals with the environment variable $PATH but I'm not entirely sure. Any help would be appreciated.

---

### Post by oldfred on 2012-06-01
I do not know python either, but have been trying to teach myself. 

My python3 boot shows both forms. And you are correct about the environment variables.

The book says you may use the  !#/usr/bin/env/python to run a specified interpeter.
And the second form  !#/usr/bin/env python is more versatile  where the shell interpreter may have a different location than /usr/bin and uses the first found entry in the shells current environment.

Did you install another copy of python, that overwrote the standard settings?

---

### Post by theigmo87 on 2012-06-01
I followed the instructions on this page:
[http://docs.python.org/using/unix.html#on-linux](http://docs.python.org/using/unix.html#on-linux)

Basically I downloaded the 2.7.3 tar ball, and followed those instructions.  I just saw the warning that states:
> make install can overwrite or masquerade the python binary. make altinstall is therefore recommended instead of make install since it only installs exec_prefix/bin/pythonversion.

this sounds like the mistake I probably made because I didn't use altinstall, but I don't know what to do to reverse it.

Reading further, I just looked at the README right above that warning and in the build instructions it states:

> Previous versions of Python used a manual configuration process that involved editing the file Modules/Setup

I'm thinking that that those configuration files were probably overwritten...

---

### Post by theigmo87 on 2012-06-01
It seems I extracted the 2.7.3 tar ball to my home directory, and ran the commands from there if that's any help. In my /usr/bin/ directory the python, python2 commands are linked to python2.7 command thats in there, and the python2-config and python-config are linked to python2.7-config. I don't know if that helps at all.

---

### Post by theigmo87 on 2012-06-01
I fixed it. I noticed that there were different python binaries in the folders "/usr/local/bin" and "/usr/bin", and the common binaries were linked slightly differently. the $PATH variable that env from the shebang uses listed "/usr/local/bin" before "/usr/bin".  

Since I used "/usr/bin/python" successfully by changing the script itself, I placed the path "/usr/bin" before "/usr/local/bin" in the $PATH variable by running "sudo nano /etc/environment" and then restarting my computer and voila, it works! 

Everything is fixed. I can successfully run the software center, ubuntu one works and all the problems with it are fixed, and my xbmc is now running the addons successfully. Thanks for the help.

---

