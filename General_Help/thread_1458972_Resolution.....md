---
title: "Resolution...."
date: 2010-04-20
forum: General Help
---

### Post by warrior_juggalo on 2010-04-20
I have installed Xubuntu and the only resolution i can get is 720 x 400, There are no other options....

I thought maybe it was just Xubuntu so i booted up slax and it's the same 720 x 400 and once again no options to change it?

I HAVE to have this fixed in 3 hours, PLEASE!!!!! help.

---

### Post by ZeroSpawn on 2010-04-20
Only way I found out how to fix my resolution is updating my xorg.conf

```
Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     4
        Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     8
        Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     15
        Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     16
        Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     24
        Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

EndSection
```

---

### Post by warrior_juggalo on 2010-04-20
Can i just copy/paste all of that into mine?

After i do that do i just go to "Display" and change it as normal?

---

### Post by ZeroSpawn on 2010-04-20
Yup, well thats what I did. Make sure you make a back up of your xorg.conf. and use:

```
sudo cp xorg.conf xorg.conf_backup
sudo nano xorg.conf
```

---

### Post by warrior_juggalo on 2010-04-21
I have this GPU, Would this have anything to do with it, [http://cgi.ebay.com/4MB-AGP-Video-Inline-Memory-Module-AIMM-133-133-/270355230397](http://cgi.ebay.com/4MB-AGP-Video-Inline-Memory-Module-AIMM-133-133-/270355230397)

---

