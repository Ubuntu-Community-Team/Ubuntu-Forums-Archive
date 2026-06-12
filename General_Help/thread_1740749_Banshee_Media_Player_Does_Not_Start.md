---
title: "Banshee Media Player Does Not Start"
date: 2011-04-27
forum: General Help
---

### Post by Morderwurst on 2011-04-27
Running banshee from terminal produces no output. I have tried removal and reinstall.

Log from banshee --debug:

[B]exec -a banshee mono  /usr/lib/banshee/Banshee.exe    --redirect-log --play-enqueued

[Info  13:47:49.746] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, i686) @ 2011-04-09 07:25:01 UTC]
[Info  13:47:57.763] Updating web proxy from GConf
[Info  13:47:57.942] All services are started 5.286448
** (Banshee:3273): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:3273): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:3273): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/sean/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:3273): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:3273): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:3273): DEBUG: Loading the real store page
[Info  13:48:01.498] nereid Client Started
[Info  13:48:01.965] GStreamer version 0.10.32.0, gapless: True, replaygain: False[/B]



Any help is appreciated!

---

### Post by techunit on 2011-04-27
```
banshee -v
```

This will run banshee in verbose mode and should yeild some useful information.

Are you sure it isn't starting in the back ground. Try going to the sound menu and see if has actually started.

You may need to purge and reinstall it. If the above doesn't yield something useful try the following commands to reinstall banshee.

```
sudo apt-get purge banshee
sudo apt-get install banshee
```

Good Luck

---

### Post by Lars Noodén on 2011-04-27
There are also other media players worth looking at including Rhythmbox, Amarok, VLC, Totem, or Exaile.

---

### Post by techunit on 2011-04-27
> **Lars Noodén said:**
> There are also other media players worth looking at including Rhythmbox, Amarok, VLC, Totem, or Exaile.
How is this relevent he just wants to get banshee working again insisting he switch isn't the way to go.

---

### Post by Lars Noodén on 2011-04-27
The media players Rhythmbox, Amarok, VLC, Totem, or Exaile are worth mentioning because they solve the problem of having a media player that works.

---

### Post by Morderwurst on 2011-04-27
> **techunit said:**
> ```
banshee -v
```This will run banshee in verbose mode and should yeild some useful information.

Are you sure it isn't starting in the back ground. Try going to the sound menu and see if has actually started.

You may need to purge and reinstall it. If the above doesn't yield  something useful try the following commands to reinstall banshee.

```
sudo apt-get purge banshee
sudo apt-get install banshee
```Good Luck

I will try to purge/reinstall when I get home, thanks.

> **Lars Noodén said:**
> There are also other media players worth looking at including Rhythmbox, Amarok, VLC, Totem, or Exaile.

Yes, I already have VLC and Amarok. I have used Rhythmbox/Totem (e.g. v10.10).

---

### Post by directhex on 2011-04-27
Looks like a U1MS bug?

---

