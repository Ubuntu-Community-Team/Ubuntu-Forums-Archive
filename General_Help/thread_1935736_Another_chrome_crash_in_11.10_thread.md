---
title: "Another chrome crash in 11.10 thread"
date: 2012-03-04
forum: General Help
---

### Post by medic8ted on 2012-03-04
This morning I was happily surfing the web using Google Chrome and decided today was a good day to "upgrade" to Ubuntu 11.10.  Boy, was I mistaken.  Now my Chrome is broke.  Every time it starts up it crashes.  Immediately.
I've been googling (unhappily via Firefox) solutions and tried what I have found to no avail.  Here's what I've done:

-Tried deleting ./config/google-chrome folder and that slows it down by about 5 seconds but it still crashes.  Tried this each time I uninstall/reinstall Chrome.
-Tried using "apt-get remove google-chrome" and reinstalling it.  Tried Chromium too.  No good.  Chromium crashes everytime too.
-Tried adding Chromium daily builds ppa and updated to daily build.  Nope.
-Tried deleting keyring entry (passwords:login) in passwords and keyrings.  Nope.  That really pisses me off because now I lost all my passwords for nothing.
-Tried enabling crash reports but it dies too quick to get a crash ID.  So Google will be of no help, as they are the almighty gurus who can do no wrong.

When run from terminal I get this:
> le/chrome/chrome: pthread_mutex_lock.c:312: __pthread_mutex_lock_full: Assertion `(-(e)) != 3 || !robust' failed.
Segmentation fault

When another user is logged in (my wife), Chrome functions completely normal!  The plot thickens.....

Doesn't matter if I log in using Unity or Gnome classic, same crash everytime.
Please help, I have been using Chrome since its initial Beta release for Linux and hate the thought of going back to Firefox.
](*,)

---

### Post by medic8ted on 2012-03-04
Update.  tried > sudo apt-get purge google-chrome and then reinstalling it.  Same problem but terminal output is now this:
> le/chrome/chrome: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.
--2012-03-04 22:44:02--  [https://clients2.google.com/cr/report](https://clients2.google.com/cr/report)
Resolving clients2.google.com... [10:16:5449469252:ERROR:platform_thread_posix.cc(264)] Not implemented reached in static void base::PlatformThread::SetThreadPriority(base::PlatformThreadHandle, base::ThreadPriority)
74.125.225.104
Connecting to clients2.google.com|74.125.225.104|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/fd/3'

    [<=>                                    ] 0           --.-K/s              
Crash dump id: cf0fd314544775f6
    [ <=>                                   ] 16          --.-K/s   in 0s      

2012-03-04 22:44:19 (147 KB/s) - `/dev/fd/3' saved [16]


---

