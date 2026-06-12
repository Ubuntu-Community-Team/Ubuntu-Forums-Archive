---
title: "Command line refreshrate"
date: 2012-04-02
forum: General Help
---

### Post by crh23 on 2012-04-02
I have an old computer on which I installed Lubuntu and when I stop  lxdm with
 ```
sudo service lxdm stop
```
to switch to command line my monitor gives the error:

    Analog
  Out Of Range
46.4 Khz / 43hz

Does anyone know how to change the refresh rate that the command line uses? I am new to Linux so sorry if I am being stupid!

crh23

---

### Post by sudodus on 2012-04-02
Welcome to the Ubuntu Forums :-)

Why do you want to run in text mode? Is it temporary or do you simply want to run in text mode because the computer cannot manage LXDE because it doesn't have the muscles.

You can select text mode at start-up by adding text at the end of the command line 'behind' the menu line in the grub menu,the first menu (text menu), where you select Ubuntu, Ubuntu (recovery mode) etc.

You can also make a persistent entry with that. See this link
[[COLOR="Red"]_http://aacable.wordpress.com/2011/06/13/ubuntu-howto-boot-into-text-mode/_[/COLOR]]("http://aacable.wordpress.com/2011/06/13/ubuntu-howto-boot-into-text-mode/")
Read more about grub
[[COLOR="red"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by crh23 on 2012-04-02
Thanks but the problem isn't accessing text mode; it is the fact that text mode doesn't display on my monitor due to the refresh rate being incorrect.

---

### Post by sudodus on 2012-04-02
> **crh23 said:**
> Thanks but the problem isn't accessing text mode; it is the fact that text mode doesn't display on my monitor due to the refresh rate being incorrect.
Is that the case also at boot? Or is the refresh rate changed by the graphics mode? Maybe you can use a boot option to set the graphics mode to something, that works on your computer. See these links
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

