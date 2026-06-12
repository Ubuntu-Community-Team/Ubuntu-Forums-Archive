---
title: "Thunderbird opens links with Chrome instead of Firefox"
date: 2011-10-17
forum: General Help
---

### Post by Monsuco on 2011-10-17
Hello, I'm running Kubuntu 11.10. I have installed Thunderbird and Firefox from apt and I have installed Chrome from Google's page. I set Firefox as my default browser and want everything to open links that I click on in Firefox. For whatever reason, Thunderbird is ignoring this setting and opens everything with Chrome. How do I get Chrome to honor my defaults?

---

### Post by lovinglinux on 2011-10-18
Try this:

[http://hsmak.wordpress.com/2009/09/03/howto-force-thunderbird-to-open-links-in-firefox/](http://hsmak.wordpress.com/2009/09/03/howto-force-thunderbird-to-open-links-in-firefox/)

---

### Post by mogliii on 2012-06-12
It seems it doesn't work at the moment.
network.protocol-handler.app.http(s) is ignored by thunderbird as of now (at least the version from the ubuntu repositories). Setting to xdg-open or any browser binary is ignored.
[http://code.google.com/p/chromium/issues/detail?id=36102](http://code.google.com/p/chromium/issues/detail?id=36102)

---

