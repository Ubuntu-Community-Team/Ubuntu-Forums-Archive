---
title: "Google Chrome suddenly shutdown with login"
date: 2012-02-23
forum: General Help
---

### Post by saidbakr on 2012-02-23
Hi,
I have Google Chrome 17.0.963.56 on Ubuntu 11.10. It usually stop responding and shut down with login on several websites such as Facebook, Google, etc.

Do you know any suggestion to solve this problem?

---

### Post by Gremlinzzz on 2012-02-23
Change browsers see if they react the same:popcorn:

---

### Post by saidbakr on 2012-02-23
> **Gremlinzzz said:**
> Change browsers see if they react the same:popcorn:
FireFox does not do the same. It works properly.

---

### Post by Gremlinzzz on 2012-02-23
How long did you have Google Chrome before it started acting strange?
did you cleanup,cookies,history. did you install something different?
might be a Google bug or something :popcorn:

---

### Post by daftlad on 2012-02-23
I have the same problem since upgrading to 11.10 before that it was fine in 10.04, 10.10, and 11.04. Tried the stable version and beta version, also tried Chromium but still shuts down when logging to facebook or other websites. Firefox and opera work ok but would prefer to use chrome.
This is what I get after starting from the terminal,

john@john-desktop:~$ google-chrome
[21027:21047:15823614114:ERROR:web_data_service.cc(677)] Cannot initialize the web database: 2

(exe:21112): Gdk-WARNING **: XID collision, trouble ahead

(exe:21112): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(exe:21112): Gdk-WARNING **: XID collision, trouble ahead

(exe:21112): Gdk-WARNING **: XID collision, trouble ahead
le/chrome/chrome: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.
--2012-02-23 20:50:19--  [https://clients2.google.com/cr/report](https://clients2.google.com/cr/report)
Resolving clients2.google.com... 173.194.34.104, 173.194.34.102, 173.194.34.101, ...
Connecting to clients2.google.com|173.194.34.104|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/fd/3'

    [<=>                                                                                                  ] 0           --.-K/s              
Crash dump id: a8e8c56be759567a
    [ <=>                                                                                                 ] 16          --.-K/s   in 0s      

2012-02-23 20:50:28 (192 KB/s) - `/dev/fd/3' saved [16]

Aborted
john@john-desktop:~$

---

### Post by Pilot6 on 2012-03-11
Exactly same here. But it happens only on one computer with radeon free drivers.

---

