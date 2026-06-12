---
title: "mozilla firefox 64-bit problems."
date: 2009-09-19
forum: General Help
---

### Post by sandyd on 2009-09-19
I downloaded the x64 bit mozilla firefox from mozilla's site thinking that it would work perfectly.

however, i ended up getting these errors
```

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

(firefox-bin:5705): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64

(firefox-bin:5705): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64

(firefox-bin:5705): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

(firefox-bin:5705): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64

(firefox-bin:5705): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64

(firefox-bin:5705): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so [/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64]                                                                                                
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: wrong ELF class: ELFCLASS64]                                                                                          
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-cone-plugin.so [/usr/lib/totem/gstreamer/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]                                                                                                              
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so [/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]                                                                                                                
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-mully-plugin.so [/usr/lib/totem/gstreamer/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so [/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libskypebuttons.so [/usr/lib/mozilla/plugins/libskypebuttons.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so [/usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so [/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-cone-plugin.so [/usr/lib/totem/gstreamer/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so [/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-mully-plugin.so [/usr/lib/totem/gstreamer/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so [/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]


```when i started firefox.

in addition to that, gtk-qt-engine didn't work with firefox causing it to be extremely ugly.

help?

and yes, i know this is related to the 64bit library bug... which i cannot find at the moment.

---

### Post by sandyd on 2009-09-19
or rather, a better question is how do i get x64 builds of firefox from mozilla?

---

### Post by Soul-Sing on 2009-09-19
imo "they" (64bit) are not available....(for linux)
do you have a linkage?

---

### Post by Slim Odds on 2009-09-19
> **carlee said:**
> I downloaded the x64 bit mozilla firefox from mozilla's site thinking that it would work perfectly.

What's wrong with the one in the Ubuntu repositories?

There are a lot of interactions between applications and libraries. The stuff in the repos has been well tested to make sure everything works right. I'd use them if I was you.

---

### Post by NoaHall on 2009-09-19
Use the safe one in the repos, and if you need a better flash, follow the link in my sig.

---

### Post by sandyd on 2009-09-19
> **leoquant said:**
> imo "they" (64bit) are not available....(for linux)
do you have a linkage?
yep

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.2/linux-i686/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.2/linux-i686/)

---

### Post by biebel on 2009-09-19
i686 is not 64 bit.

All I had to do to get flash working properly on my 64 bit ubuntu using the default firefox from the install was:
- uninstall the flash player from the repos
```

sudo apt-get remove --purge flashplugin-nonfree

```
- Download the plugin from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
- Unpack it to /home/username/.mozilla/plugins
- Restart firefox

Works almost perfectly here. Only fullscreen HQ youtube vids are choppy, but no more gray boxes where the flash vids should be.

---

### Post by sandyd on 2009-09-19
sigh.... i guess building from source it is.

---

### Post by darco on 2009-09-19
If you want an x64 bit version of FF, you need to download Shiretoko x64....
or better yet, Chromium x64

darco

---

### Post by sandyd on 2009-09-19
p.s.

if i built mozilla firefox and installed it in
/opt/mozilla/firefox , how do i get the plugins and other stuff from my old firefox install.

---

### Post by sandyd on 2009-09-19
> **darco said:**
> If you want an x64 bit version of FF, you need to download Shiretoko x64....
or better yet, Chromium x64

darco
i have Shiretoko but i kinda wanted it with the normal firefox branding.

---

