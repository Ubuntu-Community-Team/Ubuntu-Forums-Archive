---
title: "xcb_io.c:140: dequeue_pending_request"
date: 2011-06-27
forum: General Help
---

### Post by Tumaini on 2011-06-27
When running a Java based graphical application, I get the following error in Ubuntu 11.04.
It does not appear on Mac OS/X and I've seen the error occurs in cheese, spotify and other Linux apps in the latest Ubuntu release, so I think it's related to Ubuntu.

```
java: ../../src/xcb_io.c:140: dequeue_pending_request: Assertion `req == dpy->xcb->pending_requests' failed.
```What does this error mean and why does it happen?
It doesn't happen in all applications based on the libraries I use for this one application, so it must be something specific that triggers it.
Does anyone have any ideas?

---

### Post by lracicot on 2011-08-10
I have exactly the same problem when I use my laptop built-in webcam, but all is working when using an USB logitech webcam.

---

