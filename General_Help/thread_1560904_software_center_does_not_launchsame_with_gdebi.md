---
title: "software center does not launch/same with gdebi"
date: 2010-08-25
forum: General Help
---

### Post by shantiq on 2010-08-25
on a fairly new one-week old install

software center does not launch

i pick a package and click on install and nothing happens


i removed and reinstalled it and still the same


if i enter software-package in the terminal i get this

```
shantiq@shantiq-desktop:~$ software-center
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 579, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 75, in error_cb
    callback('')
  File "/usr/share/software-center/softwarecenter/backend/transactionswatcher.py", line 39, in _register_active_transactions_watch
    apt_daemon = aptdaemon.client.get_aptdaemon()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/client.py", line 897, in get_aptdaemon
    False),
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 579, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 75, in error_cb
    callback('')
  File "/usr/share/software-center/softwarecenter/backend/transactionswatcher.py", line 39, in _register_active_transactions_watch
    apt_daemon = aptdaemon.client.get_aptdaemon()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/client.py", line 897, in get_aptdaemon
    False),
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
/usr/share/software-center/softwarecenter/apt/aptcache.py:40: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main_iteration()

```


any suggestions or fix       thanx    shan


gdebi does not work either maybe those 2 problems are related


```
shantiq@shantiq-desktop:~$ gdebi
Traceback (most recent call last):
  File "/usr/bin/gdebi", line 35, in <module>
    from GDebi.GDebiCli import GDebiCli
  File "/usr/lib/python2.6/dist-packages/GDebi/GDebiCli.py", line 35, in <module>
    from DebPackage import DebPackage, Cache
  File "/usr/lib/python2.6/dist-packages/GDebi/DebPackage.py", line 26, in <module>
    import apt_inst, apt_pkg
ImportError: /usr/lib/libapt-inst-libc6.10-6.so.1.1: undefined symbol: ctTar4DoneEb
shantiq@shantiq-desktop:~$ 

```



a python 2.6 problem?

---

### Post by dv3500ea on 2010-08-25
You should report these bugs:
[Here]("https://bugs.launchpad.net/ubuntu/+source/software-center") for Ubuntu Software Centre
and [here]("https://bugs.launchpad.net/ubuntu/+source/gdebi") for gdebi.

In the meantime, you could try using Synaptic Package Manager (found in the System -> Administration menu)

---

### Post by shantiq on 2010-08-27
still no joy with either gdebi or software-center
tried complete uninstall and reinstall to no effect

now this is what i get when i reinstall software-center i hightlight in red where the problem seems to be


any ideas?

```
shantiq@shantiq-desktop:~$ sudo apt-get install software-center 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  software-center
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/279kB of archives.
After this operation, 1,720kB of additional disk space will be used.
[COLOR="Red"]apt-extracttemplates: symbol lookup error: /usr/lib/libapt-inst-libc6.10-6.so.1.1: undefined symbol: ctTar4DoneEb
debconf: apt-extracttemplates failed: Bad file descriptor[/COLOR]
Selecting previously deselected package software-center.
(Reading database ... 235876 files and directories currently installed.)
Unpacking software-center (from .../software-center_2.0.7_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up software-center (2.0.7) ...

Processing triggers for python-central ...
shantiq@shantiq-desktop:~$ 

```



and this comes up with gdebi too

---

### Post by gokulvarma on 2010-10-01
Try this link. Hope it helps.

[http://open-help.blogspot.com/2010/10/how-to-fix-software-center-problem-in.html](http://open-help.blogspot.com/2010/10/how-to-fix-software-center-problem-in.html)

---

### Post by sikander3786 on 2010-10-01
Same version python for both root and user? Or you have installed anyother version besides the default one?

Type

```

python

```

```

sudo python

```

and see which versions are installed.

---

### Post by shantiq on 2010-10-01
> **gokulvarma said:**
> Try this link. Hope it helps.

[http://open-help.blogspot.com/2010/10/how-to-fix-software-center-problem-in.html](http://open-help.blogspot.com/2010/10/how-to-fix-software-center-problem-in.html)


this is the advice they give there


I recently upgraded to "ubuntu 10.10 maverick meerkat" and I had a strange problem. My software center wont open. Well after hours of head scratching i found the solution. 

Go to "System-->preferences-->Main Menu" and select software center, click properties on the right panel. In the command box add "sudo or gksudo" at the beginning of the line.

This fixed my problem, hope it helps you too.


mine put itself right with no changes i consciously did


anyway it is solved now


thanx for the help to all

---

