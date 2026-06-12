---
title: "Firefox 3.5 how load cache to the memory ?"
date: 2010-04-03
forum: General Help
---

### Post by ubfu on 2010-04-03
How do I set firefox to load video stream such as youtube into the memory rather than disk ?
When watching a youtube clip , it cache them and load it into the hard disk.Even on other video website , it still load into the hard disk.There is a 5 min flash HD video clip 100mb , and disk size use up 100mb.
Is there a setting to configurate it to load only to the memory ? I had 2GB and ubuntu only use up 600mb.It'd be rather nice to make use of memory.

---

### Post by ron999 on 2010-04-03
Hi
I run Firefox with its cache in RAM.
I followed the instructions here:-[http://ubuntuguide.net/speed-up-firefox-by-moving-cache-into-ram-in-ubuntu]("http://ubuntuguide.net/speed-up-firefox-by-moving-cache-into-ram-in-ubuntu")

---

### Post by w8ye on 2010-04-03
There's a "ADD ON" for Fire Fox called "Download Helper" that will do this for you.

It will put a little three circle icon in the tool bar that you click on when you want to download a stream.

---

### Post by w8ye on 2010-04-03
If you go to the Ubuntu Soft Ware Center at the bottom of Applications if you are running 9.10, there is a program in the sound section called Sound Converter.

When sound converter has the proper preferences set, it can convert captured .flv stream files into .mp3 music files. You can set preferences to keep the .mp3, .flac, or .ogg files in the same directory or move them elsewhere. You can also set Sound Converter to delete the original files or leave them intact.

---

### Post by dcstar on 2010-04-03
> **ubfu said:**
> How do I set firefox to load video stream such as youtube into the memory rather than disk ?
When watching a youtube clip , it cache them and load it into the hard disk.Even on other video website , it still load into the hard disk.There is a 5 min flash HD video clip 100mb , and disk size use up 100mb.
Is there a setting to configurate it to load only to the memory ? I had 2GB and ubuntu only use up 600mb.It'd be rather nice to make use of memory.

Simply change the **browser.cache.memory.capacity** & **browser.cache.memory.enable** settings in about:config.

---

### Post by ubfu on 2010-04-06
> **w8ye said:**
> There's a "ADD ON" for Fire Fox called "Download Helper" that will do this for you.

It will put a little three circle icon in the tool bar that you click on when you want to download a stream.
I got those add on but I just intend to stream it not to download it.Just a clip.

> **dcstar said:**
> Simply change the **browser.cache.memory.capacity** & **browser.cache.memory.enable** settings in about:config.
It still write into hard disk , tried that

> **ron999 said:**
> Hi
I run Firefox with its cache in RAM.
I followed the instructions here:-[http://ubuntuguide.net/speed-up-firefox-by-moving-cache-into-ram-in-ubuntu]("http://ubuntuguide.net/speed-up-firefox-by-moving-cache-into-ram-in-ubuntu")
Thanks but it rather complicated to understand.What does every step of it means ?
```

.Edit /etc/fstab,open terminal from Applications->Accessories menu and type:

    sudo gedit /etc/fstab

Add following into this file and close it.

    tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
    tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0

2.Edit /etc/sysctl.conf:

    sudo gedit /etc/sysctl.conf

add this line and save it:

    vm.swappiness=1
```

---

