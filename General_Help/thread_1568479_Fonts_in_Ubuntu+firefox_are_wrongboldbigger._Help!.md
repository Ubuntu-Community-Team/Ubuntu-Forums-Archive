---
title: "Fonts in Ubuntu+firefox are wrong/bold/bigger. Help!"
date: 2010-09-05
forum: General Help
---

### Post by AnimeOmega on 2010-09-05
Here's how reddit looks on Arch Linux: [http://i.imgur.com/JqsLC.png](http://i.imgur.com/JqsLC.png)

Here's reddit on Ubuntu 10.04 and 10.10 Beta: [http://i.imgur.com/Cp8Er.png](http://i.imgur.com/Cp8Er.png)

Note: I installed 10.10 after I failed to get the fonts I wanted with 10.04.

Reddit is not the only site that displays fonts differently. Here is a list of things I tried so far:
    
* Installed 'ttf-mscorefonts' via 'ubuntu-restricted-extras' and a few other font packages like 'ttf-bitstream-vera', 'ttf-dejavu-extra' and 'ttf-opensymbol'.
    
* I'm using 64bit 'Firefox 3.6.9' on Arch and Ubuntu, same hardware. In Firefox I went to: Edit -> Preferences -> Content Tab and made sure both had the same things. The 'Allow pages to select their own fonts' is checked.

* I'm using 'Gnome 2.31' and went to: System -> Preferences -> Appearance -> Fonts (tab) (and -> Details...) and changed Ubuntu's default values to Arch's values.

* Googled a bit and failed, I also looked at:
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)
[http://wiki.archlinux.org/index.php/Fonts](http://wiki.archlinux.org/index.php/Fonts)
But didn't find anything to fix my issue. 

* Made sure both had the same: /etc/fonts/fonts.conf and /etc/X11/xorg.conf, ran 'sudo fc-cache -fv' and rebooted. I'm using the proprietary nvidia driver 256.53 for my Nvidia GeForce 8800 GTS 512MB.

Anyone having the same issue? Any suggestions? Ideas? Workaround? A fix? Thanks!

---

### Post by lovinglinux on 2010-09-07
In my opinion, Arch is the one with problems.

---

### Post by AnimeOmega on 2010-09-07
Having the ability to choose is awesome. I fixed it. (:

---

### Post by lovinglinux on 2010-09-07
> **AnimeOmega said:**
> Having the ability to choose is awesome. I fixed it. (:

Would you mind sharing the solution?

---

### Post by AnimeOmega on 2010-09-07
> **lovinglinux said:**
> Would you mind sharing the solution?

Sure, edit xorg.conf:

$ gksu gedit /etc/X11/xorg.conf

Add this under 'Device' in xorg.conf:

```

Option "UseEdidDpi" "FALSE"
Option "DPI" "85 x 85"

```

You can change both 85 to a DPI you find enjoyable, and yeah... changing the DPI in System -> Appearance -> ... is not the same. (at least in my case)

---

### Post by lovinglinux on 2010-09-08
> **AnimeOmega said:**
> Sure, edit xorg.conf:

$ gksu gedit /etc/X11/xorg.conf

Add this under 'Device' in xorg.conf:

```

Option "UseEdidDpi" "FALSE"
Option "DPI" "85 x 85"

```

You can change both 85 to a DPI you find enjoyable, and yeah... changing the DPI in System -> Appearance -> ... is not the same. (at least in my case)

Interesting. Thanks.

---

