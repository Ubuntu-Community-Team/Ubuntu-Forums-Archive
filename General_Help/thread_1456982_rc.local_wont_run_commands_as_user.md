---
title: "rc.local wont run commands as user"
date: 2010-04-17
forum: General Help
---

### Post by buckley310 on 2010-04-17
i have edited /etc/rc.local and i can add the command 'deluged' and it runs just fine but i need it to run under my username but when i change it to 'sudo -u sean deluged' it doesnt run deluge at startup. whats even weirder is if i run this command 'sudo sh /etc/rc.local' it runs deluge as seanjust like its supposed to. any ideas? did i miss something?

---

### Post by Brandon Williams on 2010-04-18
Are you certain that it isn't trying to start deluge and failing? Is it possible that it's a resource availability issue? perhaps for a filesystem?

I don't know what the configuration for deluge looks like, but I assume that it expects some specific directory to be available at start. If that directory is on a filesystem that isn't finished mounting yet, starting deluge might fail. If this is the case, you will want to do something to cause the script to wait until the filesystem is mounted before attempting to start deluge. You would be better off adding an upstart service launcher for this purpose, since upstart will allow you to explicitly specify that the filesystem needs to be mounted before launching deluge.

If this is not the case, then try adding these three lines to /etc/rc.local before the command line that starts deluge:
```
exec 2> /var/log/rc.local.log  # send stderr from rc.local to a log file
exec 1>&2                      # send stdout to the same log file
set -x                         # tell sh to display commands before execution
```

After startup is complete, check /var/log/rc.local.log to verify a) that it is being created, b) that your startup command is being run, and c) that there is no output to stderr or stdout indicating an error.

---

### Post by buckley310 on 2010-04-19
+ sudo -u sean deluged
Traceback (most recent call last):
  File "/usr/bin/deluged", line 8, in <module>
    load_entry_point('deluge==1.1.9', 'console_scripts', 'deluged')()
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 277, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 2180, in load_entry_point
    return ep.load()
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 1913, in load
    entry = __import__(self.module_name, globals(),globals(), ['__name__'])
  File "/usr/lib/pymodules/python2.6/deluge/main.py", line 50, in <module>
    import deluge.configmanager
  File "/usr/lib/pymodules/python2.6/deluge/configmanager.py", line 99, in <module>
    _configmanager = _ConfigManager()
  File "/usr/lib/pymodules/python2.6/deluge/configmanager.py", line 50, in __init__
    self.config_directory = deluge.common.get_default_config_dir()
  File "/usr/lib/pymodules/python2.6/deluge/common.py", line 132, in get_default_config_dir
    return xdg.BaseDirectory.save_config_path("deluge")
  File "/usr/lib/pymodules/python2.6/xdg/BaseDirectory.py", line 59, in save_config_path
    os.makedirs(path, 0700)
  File "/usr/lib/python2.6/os.py", line 150, in makedirs
    makedirs(head, mode)
  File "/usr/lib/python2.6/os.py", line 157, in makedirs
    mkdir(name, mode)
OSError: [Errno 13] Permission denied: '/root/.config'
Exception AttributeError: "'NoneType' object has no attribute 'debug'" in <bound method _ConfigManager.__del__ of <deluge.configmanager._ConfigManager instance at 0x1f8a878>> ignored


this is a log file after a boot

---

### Post by sisco311 on 2010-04-19
By default, sudo doesn't reset the user's HOME environment variable. deluged tries to access the root user's home directory ;).

Try:
```
sudo -u username -i deluged
```
or
```
su - username -c "deluged"
```

---

### Post by buckley310 on 2010-04-19
adding the "-i" got it working. THANKS :)

---

