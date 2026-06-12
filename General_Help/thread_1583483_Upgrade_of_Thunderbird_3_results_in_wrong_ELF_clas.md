---
title: "Upgrade of Thunderbird 3 results in wrong ELF class: ELFCLASS64"
date: 2010-09-27
forum: General Help
---

### Post by ELMIT on 2010-09-27
How can I fix "wrong ELF class: ELFCLASS64" ???

Updatemanager suggested to upgrade thunderbird 3 and I agreed. Now thunderbird remains in the background. When I started thunderbird from the command line I saw these errors: "wrong ELF class: ELFCLASS64"

---

### Post by andrewthomas on 2010-09-27
> **ELMIT said:**
> How can I fix "wrong ELF class: ELFCLASS64" ???

Updatemanager suggested to upgrade thunderbird 3 and I agreed. Now thunderbird remains in the background. When I started thunderbird from the command line I saw these errors: "wrong ELF class: ELFCLASS64"
what were the filenames preceeding the error message?

---

### Post by ELMIT on 2010-09-28
That is the complete output:
> /bin/sh /home/ronald/thunderbird/thunderbird
LoadPlugin: failed to initialize shared library /home/ronald/.mozilla/plugins/libflashplayer.so [/home/ronald/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xine-plugin/xineplugin.so [/usr/lib/xine-plugin/xineplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/gxine/gxineplugin.so [/usr/lib/gxine/gxineplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/gcj-4.2-81/libgcjwebplugin.so [/usr/lib/gcj-4.2-81/libgcjwebplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-basic-plugin.so [/usr/lib/totem/gstreamer/libtotem-basic-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-cone-plugin.so [/usr/lib/totem/gstreamer/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so [/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-mully-plugin.so [/usr/lib/totem/gstreamer/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so [/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so [/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]


---

### Post by andrewthomas on 2010-09-28
and I presume that you have ia32-libs? 
EDIT: I guess that you don't need them. 
```

Depends: fontconfig, psmisc, debianutils (>= 1.16), libasound2 (> 1.0.22),
         libatk1.0-0 (>= 1.29.3), libc6 (>= 2.11), libcairo2 (>= 1.6.0),
         libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>=
         2.8.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1),
         libgdk-pixbuf2.0-0 (>= 2.21.6), libglib2.0-0 (>= 2.24.0), libgtk2.0-0
         (>= 2.18.0), libhunspell-1.2-0 (>= 1.2.11), libjpeg62, libnspr4-0d (>=
         4.7.3-0ubuntu1~), libnss3-1d (>= 3.12.6), libpango1.0-0 (>= 1.14.0),
         libpixman-1-0 (>= 0.11.2), libpng12-0 (>= 1.2.13-4),
         libstartup-notification0 (>= 0.10), libstdc++6 (>= 4.1.1), libx11-6,
         libxrender1, libxt6, zlib1g (>= 1:1.1.4)
```
I would reinstall from the terminal to get a better message

```
sudo aptitude reinstall thunderbird
```

---

### Post by ELMIT on 2010-09-28
I tried this:
> sudo apt-get install ia32-libs
[sudo] password for ronald: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by andrewthomas on 2010-09-28
Does the following give any errors upon reinstall?

```
sudo aptitude update && sudo aptitude reinstall thunderbird
```

---

### Post by ELMIT on 2010-09-28
Thanks that helped.

However, there are still some other glitches:

When I started Thunderbird now, I see two windows, only the frames with transparent content window. The window title bar shows:

Google Calendar Login

3 Reminders

After closing these two ghost windows Thunderbird came up.
Another window poped up with:
An error has occured
An error occurred whne writing to the calendar Home!
[Details]
Error code: MODIFICATION_FAILED
Description:

clicking on Details... just removes the last two lines

Any idea how to fix that? Would be nice if I could have the calendar(s) of my Google personal and Google company email account here too.

---

### Post by andrewthomas on 2010-09-28
Maybe you could try:

```
sudo aptitude purge thunderbird
```then get rid of your local config files
```
rm -r ~/.thunderbird
```and reinstall
```
sudo aptitude install thunderbird
```

---

### Post by ELMIT on 2010-09-28
I removed the faulty extension, ... 


thanks for your thoughts

bye

Ronald

---

### Post by JoelOl75 on 2010-09-28
Shouldn't you be using the 64 bit version of thunderbird?  Sounds like your installing 32 bit in a 64 bit OS?

---

