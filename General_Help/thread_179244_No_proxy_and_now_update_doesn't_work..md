---
title: "No proxy and now update doesn't work."
date: 2006-05-19
forum: General Help
---

### Post by SteinbergerNate on 2006-05-19
I just got back from school where there is a proxy server that I have to connect through. I've always had no problems updateing there with the proxy settings. Now I'm home where there is no proxy at all and everything works except Synaptic and the update utility. I'm assuming that apt-get doesn't work either because when I go to update, it just sits there and doesn't download the new package info file from the repositories.

I've changed my proxy settings so that they're not looking for a proxy. This is working fine with firefox as you can see since I'm posting but I can't get anything working when it comes to packages.

---

### Post by SteinbergerNate on 2006-05-19
Ok, I just tried apt-get update and it says that it's connecting to 172.20.2.23 which is the IP of the proxy at my school. I'm pretty sure I have it set to connect directly to the internet.

Yup. Just double checked. I don't have a proxy entered. It's set to direct connection.

---

### Post by Al3xanR0 on 2006-05-19
[QUOTE=SteinbergerNate]I just got back from school where there is a proxy server that I have to connect through. I've always had no problems updateing there with the proxy settings. Now I'm home where there is no proxy at all and everything works except Synaptic and the update utility. I'm assuming that apt-get doesn't work either because when I go to update, it just sits there and doesn't download the new package info file from the repositories.

I've changed my proxy settings so that they're not looking for a proxy. This is working fine with firefox as you can see since I'm posting but I can't get anything working when it comes to packages.[/QUOTE]

If you prefer to use apt you could edit /etc/apt/apt.conf, here is mine 
```
APT::Default-Release "unstable";
APT::Cache-Limit 30000000;
APT::Get::Purge;
Acquire::cdrom::Mount "/mnt/cdrom";

ACQUIRE {
    Retries "3";
    Http {
        Proxy "http://uid:passwd@proxy.addr.com:80/";
    }
};

```

of course you will have substitute uid for your actual user id and passwd for your actual password.

Hope this works.

---

### Post by SteinbergerNate on 2006-05-24
Ok, I looked in that and it does still have the old proxy settings in it. Will this file also set the proxy settings for Synaptic as well or is there a separate file for that? I found the setting for that under the menus in Synaptic but it still just sits there and doesn't look like it can download the list files.

---

### Post by SteinbergerNate on 2006-05-26
I answered my own question. I looks like that conf file is for all the package management. Everything works now. Now if I could just figure out how to get WEP to work.

---

