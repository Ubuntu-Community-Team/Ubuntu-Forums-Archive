---
title: "3d stuff on new Ubuntu upgrade?"
date: 2009-09-18
forum: General Help
---

### Post by chaotzu on 2009-09-18
Was wanting help trying to find how to enable cool graphics things like 3d cube and wobbly windows and stuff. I have compiz-fusion I just don't know where the options for it are. Hope this is an easy answer, thanks.

---

### Post by Miyavix3 on 2009-09-18
```
aptitude search compiz
```

Then find something that looks like Compiz Settings Manager

Then when you find it type:

```
sudo apt-get install compizconfig-settings-manager
```

After that, it should be in your menu.

[http://packratstudios.com/index.php/2008/03/05/how-to-install-the-compiz-setting-manager-in-ubuntu/](http://packratstudios.com/index.php/2008/03/05/how-to-install-the-compiz-setting-manager-in-ubuntu/) for more info

---

### Post by chaotzu on 2009-09-19
thanks that's what I was looking for.

---

### Post by chaotzu on 2009-09-19
Um so I was messing around with the settings and when I got to Wobbly Windows my computer froze and when I restarted my duel monitor display went back to single monitor and my configuration options are gone. If I go to display it says "it appears that your graphics driver does not support the necessary extensions to use this tool" then has me open nvidia xconfigure, but tells me that I'm not using nvidia x driver. Um what should I do?

---

### Post by zaduma on 2009-09-19
> **chaotzu said:**
> Um so I was messing around with the settings and when I got to Wobbly Windows my computer froze and when I restarted my duel monitor display went back to single monitor and my configuration options are gone. If I go to display it says "it appears that your graphics driver does not support the necessary extensions to use this tool" then has me open nvidia xconfigure, but tells me that I'm not using nvidia x driver. Um what should I do?


make sure driver is installed, try reinstalling.

---

