---
title: "Minefield Flash Plugin."
date: 2011-02-24
forum: General Help
---

### Post by Keyoto on 2011-02-24
Hello, I recently switched to Ubuntu from Windows. And I installed the .tar.bz2 archive of Minefield, and extracted the Firefox folder inside to my home directory (I didn't know if there was a place where Ubuntu stores program files like there is in Windows) I have a problem though I can't seem to get a flash plugin working with it. Before installing Minefield I used (and had flash working with) Firefox and Chromium, so I have Adobe flash and Gnash installed however neither works with Minefield. Is it because of where I installed it or is there something I'm missing? Thanks in advance for the help.

---

### Post by thefasterblueone on 2011-02-24
You could try FlashAid, seems to fix alot of flash errors.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

---

### Post by Keyoto on 2011-02-24
> **thefasterblueone said:**
> You could try FlashAid, seems to fix alot of flash errors.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)
That didn't help, Minefield still says I don't have a Flash plugin. Could it have anything to do with where I installed it?

---

### Post by 3rdalbum on 2011-02-24
Inside the hidden ".minefield" folder in your home directory, there should be a 'plugins' folder. Put the Flash plugin there.

---

### Post by Keyoto on 2011-02-24
> **3rdalbum said:**
> Inside the hidden ".minefield" folder in your home directory, there should be a 'plugins' folder. Put the Flash plugin there.
I don't have a .minefield folder, I have a .Mozilla which then has Extensions and Firefox folder niether of which have a plugins folder no matter how deep in I dig. Does that mean I installed it wrong?

---

### Post by Keyoto on 2011-02-25
I don't know if this will help at all all but I tried uninstalling and reinstalling into my /usr/local folder and when I opened it via the termal I got these erros
```


(firefox-bin:5740): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(firefox-bin:5740): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

(firefox-bin:5740): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(firefox-bin:5740): Gtk-WARNING **: Loading IM context type 'ibus' failed

(firefox-bin:5740): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(firefox-bin:5740): Gtk-WARNING **: Loading IM context type 'ibus' failed

(firefox-bin:5740): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(firefox-bin:5740): Gtk-WARNING **: Loading IM context type 'ibus' failed
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-cone-plugin.so [/usr/lib/mozilla/plugins/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so [/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-mully-plugin.so [/usr/lib/mozilla/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so [/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: wrong ELF class: ELFCLASS64]

```

---

