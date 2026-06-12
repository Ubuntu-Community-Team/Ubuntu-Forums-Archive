---
title: "Apache + PHP xdebug + fcgid = read data timeout in 40 seconds"
date: 2009-12-18
forum: General Help
---

### Post by miguelcudaihl on 2009-12-18
I'm running Apache worker + PHP5.3 + xdebug + mod_fcgid on Linux Mint Helena. My debugging sessions are limited to only 40 seconds in which the error message below is raised:

mod_fcgid: read data timeout in 40 seconds

I've searched around the already and there's one topic regarding fcgid mod global configuration being overridden inside a VirtualHost directive ([http://jay.vox.com/library/post/mod_...-settings.html]("http://jay.vox.com/library/post/mod_fcgid-ignoring-fastcgi-config-settings.html")).

However, I've already set IPCCommTimeout to 360 seconds in both the fcgid configuration and inside my VirtualHost's configuration. I've restarted apache2, restarted Mint and I'm still limited to 40 seconds of debugging.


Although I've fixed this by downloading and compiling the latest mod_fcgid source from Apache's site, I thought I should still log this as this seems to be an issue with the fcgid module

---

