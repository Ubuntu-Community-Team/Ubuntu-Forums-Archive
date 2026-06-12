---
title: "Google chrome issue"
date: 2011-12-16
forum: General Help
---

### Post by ds5v50 on 2011-12-16
I am not sure if this the right place for this but I am really frustrated by this.  Here we go, Whenever I try to open a web page with google chrome that requires some type of login the browser abruptly closes.  If I run chrome in debug I get the following error.

```
google-chrome -debugprint
le/chrome/chrome -debugprint: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.
Aborted

```

  I do not know where to start, but any help would be greatly appreciated.

---

### Post by lechien73 on 2011-12-16
Is this the issue? [http://code.google.com/p/chromium/issues/detail?id=101160](http://code.google.com/p/chromium/issues/detail?id=101160)

Seems like a bug in the keyring, if so.

---

### Post by ds5v50 on 2011-12-16
> **lechien73 said:**
> Is this the issue? [http://code.google.com/p/chromium/issues/detail?id=101160](http://code.google.com/p/chromium/issues/detail?id=101160)

Seems like a bug in the keyring, if so.


  Yes..  that appears to be the issue. I really need to brush up on my searches. Thank you for pointing me to that report.

---

### Post by lechien73 on 2011-12-16
You're welcome. I hope you can apply the workarounds and patches to solve the issue :)

---

