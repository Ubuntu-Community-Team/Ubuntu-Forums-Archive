---
title: "Banshee error"
date: 2011-07-11
forum: General Help
---

### Post by astrov on 2011-07-11
Hi,

Ive upgraded to Ubuntu 11, but on the new desktop Banshee would not start up. 
Im pretty new, handle please with consideration. :)

I got the following msg:

peter@peter-Latitude-D630:~$ banshee
[Info  21:44:21.482] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-06-28 05:46:57 UTC]
[Info  21:44:22.645] Updating web proxy from GConf
[Info  21:44:22.686] All services are started 0.988617
** (Banshee:9554): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:9554): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:9554): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/peter/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:9554): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:9554): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:9554): DEBUG: Loading the real store page

** (Banshee:9554): WARNING **: Got less number of items in credentials hash table than expected!
[Info  21:44:24.066] nereid Client Started
[Info  21:44:24.147] GStreamer version 0.10.32.0, gapless: True, replaygain: False

Unhandled Exception: GLib.GException: Can't recursively copy directory
  at GLib.FileAdapter.Move (File destination, FileCopyFlags flags, GLib.Cancellable cancellable, GLib.FileProgressCallback progress_callback) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Gio.Directory.Move (Hyena.SafeUri from, Hyena.SafeUri to) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Directory.Move (Hyena.SafeUri from, Hyena.SafeUri to) [0x00000] in <filename unknown>:0 
  at Banshee.Podcasting.PodcastService.<DelayedInitialize>m__11 () [0x00000] in <filename unknown>:0 
peter@peter-Latitude-D630:~$

---

