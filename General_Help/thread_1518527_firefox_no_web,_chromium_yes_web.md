---
title: "firefox no web, chromium yes web"
date: 2010-06-26
forum: General Help
---

### Post by jon zendatta on 2010-06-26
hell0. I have an Acer Aspire 5740, I'm currently using Chromium browser because Firefox times out & cannot access the web.I prefer to use Firefox. Any ideas please

---

### Post by lovinglinux on 2010-06-27
Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
You can also disable ipv6 on the system. See [How to disableIPv6 in Karmic Koala and Lucid Lynx](http://wojox.homelinux.org/?p=46)

For more Firefox tweaks and tips see [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)
For additional support see [Firefox Optimization and Troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by jon zendatta on 2010-08-08
yes that works. thanks:KS

---

### Post by lovinglinux on 2010-08-08
> **jon zendatta said:**
> yes that works. thanks:KS

You are welcome.

---

