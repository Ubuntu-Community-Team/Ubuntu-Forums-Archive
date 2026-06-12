---
title: "screwed up proxy settings"
date: 2012-03-01
forum: General Help
---

### Post by TheHimself on 2012-03-01
In the past I changed proxy settings in Xubuntu (probablu using the export command; I can't remember). Now I have a direct internet connection and when I use apt-get or similar commands, it tries in vein to connect to the proxy server. There is nothing in the .bashrc file related to this. Where do you think I should look?

---

### Post by Tiganjero on 2012-03-01
Did you try disabling it in Internet Explorer? Just kidding, try looking in ***/ect/apt/apt.conf*** or if there's nothing there, see if you can find an occurrence of part of your proxy setting. You can do that by executing: ```
grep -i -n "proxy_ip" *
``` Hope this helps!

Cheers,
George

---

### Post by TheHimself on 2012-03-01
Thank you! It was in the file "environment". It think I have to restart now.

---

### Post by TheHimself on 2012-03-01
I restarted but apt-get still looks for the proxy server.

---

