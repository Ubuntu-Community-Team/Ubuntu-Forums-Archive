---
title: "Google Chrome 4.0.213.1 and Flash"
date: 2009-09-28
forum: General Help
---

### Post by tom.swartz07 on 2009-09-28
Hi all

I was wondering if anyone could help me solve a problem with flash on my 64bit Ubuntu system.

I installed the unstable dev release of Google Chrome, and everywhere that Ive read, everyone says that flash works perfectly for them.

Ive installed it, tried using the --enable-plugins flag, I even tried copying libflashplayer.so to a plugins folder in /opt/google/chrome/plugins

so far, when i load up a youtube video, it gets to the page, but no video loads. It doesnt flash the warning asking to install missing plugins, either...

Does anyone know what Im doing wrong?

In the about:plugins page in chrome, there are a TON of plugins listed;
Java uses libnpjp
VLC uses libvlcplugin
and most importantly,
Flash is listed using libswfdecmozilla.so

I think that this is where the problem is occurring, yet im a little unsure if I should uninstall swfdec and lose flash for my entire system.


Dont forget- I am using 64bit ubuntu- i understand that this causes a ton of problems with 'regular' flash installations.


Thanks!

---

### Post by Giblet5 on 2009-09-28
There are problems running Flash on x64 linux.

You might want to try Adobe's alpha release of Flash 10 for x64.

[Via this site]("http://labs.adobe.com/downloads/flashplayer10.html").

---

### Post by NoaHall on 2009-09-28
Follow the advice in the link in my sig.

---

### Post by ajgreeny on 2009-09-28
On a 32 bit system I would strongly suggest you get rid of swfdec completely, as it seems to cause nothing but problems, and unless you simply can not use proprietary packages, use the adobe-flashplugin.  On a 64 bit system it may not be as simple, but do a bit of a search on this as a possibility.

---

### Post by tom.swartz07 on 2009-09-28
> **ajgreeny said:**
> On a 32 bit system I would strongly suggest you get rid of swfdec completely, as it seems to cause nothing but problems, and unless you simply can not use proprietary packages, use the adobe-flashplugin.  On a 64 bit system it may not be as simple, but do a bit of a search on this as a possibility.


Thanks for the great tips. Im going to try to remove swfdec and get the 64bit alpha from Adobe.

I remember I ran into some problems last time with flash and firefox 3.5 because 3.0.11 is the 'canonical' version and 3.5 couldnt recognize the files.
Ill post back if something happens, or if it works!

Thanks!
Tom

---

### Post by tom.swartz07 on 2009-09-28
Sweet deal!

I removed swfdec as much as I could through the terminal. I was able to remove swfdec-mozilla and swfdec-firefox, and there were some other dependencies that i was able to use autoremove to get. 

After I cleaned it up, I downloaded the 64bit alpha flash player from Adobe. I extracted it, and used
```
$ sudo mkdir /opt/google/chrome/plugins/
sudo cp /location/of/libflashplayer.so /opt/google/chrome/plugins/ 
```

I fired up Chrome, and it works like a charm!

Thanks everyone!

---

