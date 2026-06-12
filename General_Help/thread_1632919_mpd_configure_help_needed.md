---
title: "mpd configure help needed"
date: 2010-11-28
forum: General Help
---

### Post by Neon612 on 2010-11-28
I've tried following some of the tutorials around here on searching through google but I still keep getting the same error.

```
mpd --create-db

listen: Failed to listen on 127.0.0.1 (line 27): Address already in use
Aborted

```


heres my mpdconf
```
# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory		"/home/darin/Music"
playlist_directory	"/home/darin/.mpd/playlists"
db_file			"/home/darin/.mpd/mpd.db"
log_file		"/home/darin/.mpd/mpd.log"
error_file		"/home/darin/.mpd/errors.log"
pid_file		"/home/darin/.mpd/pid"
################################################################

######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "darin"
#
# The address and port to listen on.
#
bind_to_address                 "127.0.0.1"
#port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################
```

Any help will be appreciated. Thank you.

---

### Post by WorMzy on 2010-11-28
I haven't specified an address in my mpd.conf, so try commenting that out. Also, make sure that mpd isn't already running by attempting to stop it:
```
sudo /etc/init.d/mpd stop
```
Or, if that gives you an error (other than "FAIL" due to mpd not running): 
```
sudo service mpd stop
```

---

