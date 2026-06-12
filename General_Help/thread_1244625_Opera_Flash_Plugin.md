---
title: "Opera Flash Plugin"
date: 2009-08-19
forum: General Help
---

### Post by herriojr on 2009-08-19
So, I am able to get flash working in Firefox, but I can't get it to work in opera.

I've done the following:

> sudo apt-get install flashplugin-installer
> sudo ln -s /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/opera/plugins/
> ls -l
total 0
lrwxrwxrwx 1 root root 48 2009-08-19 13:32 libflashplayer.so -> /usr/lib/flashplugin-installer/libflashplayer.so

In opera, I restart the browser (shut it down, and then open again), and I get the following when I navigate to opera:plugins :
Shockwave
Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/opera/plugins/libflashplayer.so


For some reason, I can't do anything to get flash to work on Opera.  I've already read through a lot of similar issues on these boards, but I haven't found anything that works.  I've searched Synaptic Package Manager for "flash" and "swf" and I've only found that I have flashplugin-installer installed on my machine.  Any suggestions?

---

