---
title: "Spotify Linux Preview - Libnotify Notifications?"
date: 2012-09-26
forum: General Help
---

### Post by A4orce84 on 2012-09-26
Hey Guys,

I'm trying to get notifications working when spotify changes tracks. I saw the following page that described this:

[http://code.google.com/p/spotify-notify/](http://code.google.com/p/spotify-notify/)

But I'm having trouble with this. I have Spotify installed and its working and playing music with no issues. I just want the libnotify to alert me when songs change.

Is there an "official" easy way to do this?

Thanks.

--Asif

---

### Post by kostkon on 2012-09-26
> **A4orce84 said:**
> Hey Guys,

I'm trying to get notifications working when spotify changes tracks. I saw the following page that described this:

[http://code.google.com/p/spotify-notify/](http://code.google.com/p/spotify-notify/)

But I'm having trouble with this. I have Spotify installed and its working and playing music with no issues. I just want the libnotify to alert me when songs change.

Is there an "official" easy way to do this?

Thanks.

--Asif
Could you be more specific about your problems with spotify-notify? Download its latest version, extract the two files somewhere in your home folder, and then add the python file to your startup applications by typing, for example,
```
python ~/.spotify-notify/spotify-notify.py -s
```
(as you can see I put the two files in the hidden folder .spotify-notify in my home folder ;))
in the *Command* text field. For *Name*, just put Notify-Spotify and also put a comment if you want.

Then logout and login again to test it.

---

### Post by monguin61 on 2013-03-07
I'm trying to use spotify-notify as well. I have two problems: first, the notification disappears immediately - I think I fixed this by changing the "2'" in the self.notifyservice.Notify() call to "5000", but I don't know if there is a better way to fix this. Second, and more significant, the program seems to die after running for a minute or so. I ran it with python's -v option, and I saw the output listed below, after all the "import" lines. I don't see any explicit error messages, so I don't know if it's crashing or what, can anyone suggest a way to prevent this?

I am running linux mint, so if that is the cause I suppose I can just accept that it won't work properly for me.

output of python -v spotify-notify.py
```
Spotify-notify v0.6
Changing track : Metric | Lost Kitten | Synthetica (2012)
# clear __builtin__._
# clear sys.path
# clear sys.argv
# clear sys.ps1
# clear sys.ps2
# clear sys.exitfunc
# clear sys.exc_type
# clear sys.exc_value
# clear sys.exc_traceback
# clear sys.last_type
# clear sys.last_value
# clear sys.last_traceback
# clear sys.path_hooks
# clear sys.path_importer_cache
# clear sys.meta_path
# clear sys.flags
# clear sys.float_info
# restore sys.stdin
# restore sys.stdout
# restore sys.stderr
# cleanup __main__
# cleanup[1] _bisect
# cleanup[1] subprocess
# cleanup[1] sysconfig
# cleanup[1] gc
# cleanup[1] indicate
# cleanup[1] xml
# cleanup[1] collections
# cleanup[1] zipimport
# cleanup[1] gtk
# cleanup[1] gtk._lazyutils
# cleanup[1] dbus
# cleanup[1] xml.parsers
# cleanup[1] dbus.mainloop
# cleanup[1] signal
# cleanup[1] cairo
# cleanup[1] xml.parsers.expat
# cleanup[1] abc
# cleanup[1] urllib
# cleanup[1] glob
# cleanup[1] math
# cleanup[1] exceptions
# cleanup[1] _sysconfigdata_nd
# cleanup[1] _functools
# cleanup[1] _locale
# cleanup[1] pickle
# cleanup[1] itertools
# cleanup[1] marshal
# cleanup[1] dbus._expat_introspect_parser
# cleanup[1] __future__
# cleanup[1] _collections
# cleanup[1] cairo._cairo
# cleanup[1] dbus._version
# cleanup[1] dbus.exceptions
# cleanup[1] dbus._compat
# cleanup[1] array
# cleanup[1] select
# cleanup[1] _heapq
# cleanup[1] dbus.proxies
# cleanup[1] dbus._dbus
# cleanup[1] sre_constants
# cleanup[1] _warnings
# cleanup[1] _codecs
# cleanup[1] gtk._gtk
# cleanup[1] _sysconfigdata
# cleanup[1] _struct
# cleanup[1] keyword
# cleanup[1] posix
# cleanup[1] fnmatch
# cleanup[1] site
# cleanup[1] pyexpat
# cleanup[1] strop
# cleanup[1] gettext
# cleanup[1] dbus.connection
# cleanup[1] urllib2
# cleanup[1] gtk.deprecation
# cleanup[1] gio._gio
# cleanup[1] dbus.types
# cleanup[1] sitecustomize
# cleanup[1] dbus.bus
# cleanup[1] _weakref
# cleanup[1] urlparse
# cleanup[1] _weakrefset
# cleanup[1] _dbus_glib_bindings
# cleanup[1] indicate._indicate
# cleanup[1] heapq
# cleanup[1] dbus.mainloop.glib
# cleanup[1] random
# cleanup[1] dbus.lowlevel
# cleanup[1] httplib
# cleanup[1] bisect
# cleanup[1] locale
# cleanup[1] encodings
# cleanup[1] logging
# cleanup[1] socket
# cleanup[1] traceback
# cleanup[1] operator
# cleanup[1] _socket
# cleanup[1] copy
# cleanup[1] hashlib
# cleanup[1] apport_python_hook
# cleanup[1] encodings.aliases
# cleanup[1] mimetools
# cleanup[1] _random
# cleanup[1] encodings.ascii
# cleanup[1] encodings.utf_8
# cleanup[1] functools
# cleanup[1] tempfile
# cleanup[1] ssl
# cleanup[1] threading
# cleanup[1] cStringIO
# cleanup[1] base64
# cleanup[1] atexit
# cleanup[1] rfc822
# cleanup[1] fcntl
# cleanup[1] _hashlib
# cleanup[1] codecs
# cleanup[1] struct
# cleanup[1] thread
# cleanup[1] weakref
# cleanup[1] binascii
# cleanup[1] _ssl
# cleanup[2] gobject._gobject
# cleanup[2] pyexpat.errors
# cleanup[2] string
# cleanup[2] textwrap
# cleanup[2] pango
# cleanup[2] pyexpat.model
# cleanup[2] gio.unix
# cleanup[2] gobject.propertyhelper
# cleanup[2] re
# cleanup[2] optparse
# cleanup[2] UserDict
# cleanup[2] atk
# cleanup[2] glib._glib
# cleanup[2] os
# cleanup[2] _sre
# cleanup[2] gtk.gdk
# cleanup[2] posixpath
# cleanup[2] errno
# cleanup[2] os.path
# cleanup[2] gio
# cleanup[2] glib
# cleanup[2] _dbus_bindings
# cleanup[2] pangocairo
# cleanup[2] sre_parse
# cleanup[2] copy_reg
# cleanup[2] sre_compile
# cleanup[2] gobject.constants
# cleanup[2] linecache
# cleanup[2] gobject.option
# cleanup[2] _abcoll
# cleanup[2] genericpath
# cleanup[2] stat
# cleanup[2] warnings
# cleanup[2] types
# cleanup[2] time
# cleanup[2] gobject
# cleanup[2] glib.option
# cleanup sys
# cleanup __builtin__
PyThreadState_Clear: warning: thread still has a frame
# cleanup ints: 301 unfreed ints
# cleanup floats: 35 unfreed floats

```

---

