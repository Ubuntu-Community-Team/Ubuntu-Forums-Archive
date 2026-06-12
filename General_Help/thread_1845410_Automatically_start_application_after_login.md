---
title: "Automatically start application after login?"
date: 2011-09-17
forum: General Help
---

### Post by snakyjake on 2011-09-17
How do I automatically start an application (i.e. internet browser) after I login?

I need some VERY simply instructions. And I need this for all users who log into the computer.

Is there an application I can install to help with the configuration?

Thanks,
Jake
Lubuntu

---

### Post by 2F4U on 2011-09-17
In Kubuntu there is a personal settings dialogue to configure the desktop. This has an option Startup and Shutdown and there you could add Autostart programs. However, as I understand it, this is a per user setting and you would have to do it for every user.

---

### Post by sikander3786 on 2011-09-17
> **snakyjake said:**
> How do I automatically start an application (i.e. internet browser) after I login?

I need some VERY simply instructions. And I need this for all users who log into the computer.

Is there an application I can install to help with the configuration?

Thanks,
Jake
Lubuntu
There might be other methods as well but you can simply copy the respective .desktop from /usr/share/applications to /etc/xdg/autostart e.g. in case of Firefox:

```
sudo cp /usr/share/applications/firefox.desktop /etc/xdg/autostart
```

---

