---
title: "Can't get any twitter apps working (Gwibber, choqok) on Karmic"
date: 2011-04-26
forum: General Help
---

### Post by ray field on 2011-04-26
I'm running Karmic on an Asus netbook and can't get one single Twitter app working -- all of them fail on authentication.

choqok goes

```
kdeinit4: preparing to launch /usr/lib/kde4/kio_http.so
findServiceByDesktopPath: kded/networkstatus.desktop not found
findServiceByDesktopPath: kded/networkstatus.desktop not found
```

as the authentication times out.

when I try to "authorize" gwibber, it simply stops instead of bringing up a Twitter screen.

```

Traceback (most recent call last):
  File "/usr/share/gwibber/plugins/twitter/gtk/twitter/__init__.py", line 76, in on_twitter_auth_clicked
    web.load_uri(url)
AttributeError: 'webkit.WebView' object has no attribute 'load_uri'
```


Twitter works fine via the web, and all those apps work great on my desktop running Lucid.

---

