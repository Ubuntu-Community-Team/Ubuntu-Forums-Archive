---
title: "GPodder Ignores Proxy"
date: 2012-07-22
forum: General Help
---

### Post by theexternvoid on 2012-07-22
I set my HTTP proxy in the system settings. Doing echo $http_proxy shows that it is set properly. When I run GPodder from the command line then it works fine.

But if I launch it from its desktop icon like a normal Gnome app then it doesn't work. It's as if the proxy environment variable isn't loaded unless I launch from the command line. Any ideas to fix this??

---

### Post by theexternvoid on 2012-07-25
I finally solved it. GPodder unfortunately removed the ability to configure proxy stuff in its own settings. Instead it relies on the operating system's settings. You'd think it would use the Gnome proxy settings, but it doesn't! It only uses the http_proxy environment variable. Ubuntu somehow sets this variable when launching bash, but when launching an X session (via SSH) or a Gnome desktop session, that variable is not set.  Solution: add http_proxy to ~/.pam_environment.

---

