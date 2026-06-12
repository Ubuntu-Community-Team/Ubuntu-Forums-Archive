---
title: "Ubuntu Software Center Ignores Proxy Setting"
date: 2010-04-24
forum: General Help
---

### Post by afz12 on 2010-04-24
Ubuntu 9.10 10.04 "software center" seems like a good idea compared to the previous implementation but it ignores proxy settings under system->preferences->network proxy and system->administration->synaptic package manager->settings->preferences->network.

Other sections of Ubuntu work fine through the proxy e.g. web browsers and using synaptic directly. However sudo apt-get install doesn't work through a terminal on Ubuntu 10.04 beta despite all updates. The problem is definitely in Ubuntu as some parts of it recognize the proxy settings and other parts don't. This disconnection appears to be worse in U10.04 compared to U9.10 but earlier distributions (from memory) never had this problem.

Is there a "fix" I can use to get Ubuntu 10.04 to recognize the proxy settings across all its features?

---

### Post by dcstar on 2010-04-25
> **afz12 said:**
> Ubuntu 9.10 10.04 "software center" seems like a good idea compared to the previous implementation but it ignores proxy settings under system->preferences->network proxy and system->administration->synaptic package manager->settings->preferences->network.

Other sections of Ubuntu work fine through the proxy e.g. web browsers and using synaptic directly. However sudo apt-get install doesn't work through a terminal on Ubuntu 10.04 beta despite all updates. The problem is definitely in Ubuntu as some parts of it recognize the proxy settings and other parts don't. This disconnection appears to be worse in U10.04 compared to U9.10 but earlier distributions (from memory) never had this problem.

Is there a "fix" I can use to get Ubuntu 10.04 to recognize the proxy settings across all its features?

The Gnome proxy setting is used by all Gnome proxy aware apps, command line programs are not Gnome programs and do not use this setting.

The whole point about providing a GUI app that uses these setting is so people do not have the issues with command line apps which require the command line environment to be set.

---

### Post by gmargo on 2010-04-25
I don't know about a universal fix, but you can get the command line tools (apt-get, aptitude) to work by adding the following line to the **/etc/apt/apt.conf** file (create the file if it does not exist).  Substitute your appropriate proxy address.

```

Acquire::http::Proxy    "http://proxy.example.com:8080/";

```

---

### Post by airtonix on 2010-05-26
In Karmic the GUI Proxy Config (System > Preferences > Network Proxy) would edit three places : 

**/etc/apt/apt.conf**
fills this with : 
```
Acquire::http::Proxy    "http://proxy.example.com:8080/";
```

**$http_proxy & $https_proxy**
fills these variables with : 
```
"http://proxy.example.com:8080/"
```

**Gconf > /system/http_proxy**
 /host = proxy.example.com
 /port = 8080


Now it only modifies the gconf settings.

---

