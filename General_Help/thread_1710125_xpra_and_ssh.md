---
title: "xpra and ssh"
date: 2011-03-19
forum: General Help
---

### Post by kavafis on 2011-03-19
Hello, 

I've got a problem with xpra. What I would like to do is to start an xpra session on a server and then log in from a remote machine to start x applications and being able to log out and close the server connection but having the x application continue to run. Then attach to the xpra session from the remote machine again.

I'm trying to connect to an xpra session via ssh in the following way:

1. on local machine: 'ssh -Y host'
2. on the "server": 'xpra start :20'
3.close the ssh connection and reattach with 'xpra attach ssh:host:20'

it says 'attached' and then prompts me for the password but after typing it nothing happens. when ctrl+c it says:

Shutting down main-loop
Traceback (most recent call last):
  File "/usr/bin/xpra", line 6, in <module>
    xpra.scripts.main.main(__file__, sys.argv)
  File "/usr/lib/python2.6/dist-packages/xpra/scripts/main.py", line 84, in main
    run_client(parser, options, args)
  File "/usr/lib/python2.6/dist-packages/xpra/scripts/main.py", line 157, in run_client
    app.run()
  File "/usr/lib/python2.6/dist-packages/xpra/client.py", line 301, in run
    gtk.main()
KeyboardInterrupt

And this is the xpra log file:

[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
5 XSELINUXs still allocated at reset
SCREEN: 0 objects of 72 bytes = 0 total bytes 0 private allocs
DEVICE: 4 objects of 16 bytes = 64 total bytes 0 private allocs
CLIENT: 0 objects of 160 bytes = 0 total bytes 0 private allocs
WINDOW: 0 objects of 24 bytes = 0 total bytes 0 private allocs
PIXMAP: 1 objects of 8 bytes = 8 total bytes 0 private allocs
GC: 0 objects of 44 bytes = 0 total bytes 0 private allocs
CURSOR: 0 objects of 4 bytes = 0 total bytes 0 private allocs
CURSOR_BITS: 0 objects of 4 bytes = 0 total bytes 0 private allocs
DBE_WINDOW: 0 objects of 12 bytes = 0 total bytes 0 private allocs
TOTAL: 5 objects, 72 bytes, 0 allocs
4 DEVICEs still allocated at reset
DEVICE: 4 objects of 16 bytes = 64 total bytes 0 private allocs
CLIENT: 0 objects of 160 bytes = 0 total bytes 0 private allocs
WINDOW: 0 objects of 24 bytes = 0 total bytes 0 private allocs
PIXMAP: 1 objects of 8 bytes = 8 total bytes 0 private allocs
GC: 0 objects of 44 bytes = 0 total bytes 0 private allocs
CURSOR: 0 objects of 4 bytes = 0 total bytes 0 private allocs
CURSOR_BITS: 0 objects of 4 bytes = 0 total bytes 0 private allocs
DBE_WINDOW: 0 objects of 12 bytes = 0 total bytes 0 private allocs
TOTAL: 5 objects, 72 bytes, 0 allocs
1 PIXMAPs still allocated at reset
PIXMAP: 1 objects of 8 bytes = 8 total bytes 0 private allocs
GC: 0 objects of 44 bytes = 0 total bytes 0 private allocs
CURSOR: 0 objects of 4 bytes = 0 total bytes 0 private allocs
CURSOR_BITS: 0 objects of 4 bytes = 0 total bytes 0 private allocs
DBE_WINDOW: 0 objects of 12 bytes = 0 total bytes 0 private allocs
TOTAL: 1 objects, 8 bytes, 0 allocs
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
/usr/lib/python2.6/dist-packages/wimpiggy/wm.py:9: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  118 (X_SetModifierMapping)
  Value in failed request:  0x17
  Serial number of failed request:  21
  Current serial number in output stream:  21
New connection received
Connection lost
New connection received
Connection lost
New connection received
Handshake complete; enabling connection
Connection lost

Any help would be greatly appreciated! I'm using ubuntu 10.10 on both machines.

---

