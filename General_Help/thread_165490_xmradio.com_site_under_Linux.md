---
title: "xmradio.com site under Linux"
date: 2006-04-24
forum: General Help
---

### Post by mark748 on 2006-04-24
For those of you using the xmradio.com website to listen to you're xm radio online, has anybody tried to configure you're Firefox, it seems you need some Windows Media player plugin or player, I tried to use Kaffeine, but doesn't seem configurable.
:-k

---

### Post by kris kincaid on 2006-04-24
I am listening right now with the mplayer-plugin. It takes about 3 minutes for the stream to start, but it eventually works.

---

### Post by mark748 on 2006-04-24
Thanks Kris.

;) I found by installing the easy Ubuntu 2.4 beta 3, it added something to my Firefox to allow me to stream the Xmradio.com broadcasts, but seems a little buggy, it works, but sometimes when selecting presets or changing bandwidth, it closes down the browser. But I'm happy.

Mark

---

### Post by fake123 on 2006-05-11
[QUOTE=kris kincaid]I am listening right now with the mplayer-plugin. It takes about 3 minutes for the stream to start, but it eventually works.[/QUOTE]
sorry for the bump, but how do you do this?

---

### Post by kris kincaid on 2006-05-11
It's been so long since I installed all the add on programs like the m player plug-in, I have forgotten. I am pretty sure Automatrix installed everthing I needed, and it just worked. I think I tried it the first time, and it didn't immediately work, so I just went on to something else. The, about three minutes later, the stream started to play. Ya just gotta be patient. :cool: 

Automatrix download:

[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

---

### Post by Kobalt on 2006-05-12
In command line : 
```
$ sudo apt-get install mplayer-<your architecture>
```
```
$ sudo apt-get install mozilla-mplayer
```

---

### Post by averydedog on 2006-08-09
Automatix did indeed install everything I needed to hear XM online.  For some reason, itr stopped working.  I think it happened after an update to mplayer.  

Anyone have an idea where I should look to fix it?

---

### Post by liquoredolce on 2007-07-17
Sorry for bumping this thread, I know it's old but I'm having the same problem.  I installed the mplayer-plugin and it worked perfectly the first time I tried to play XM, but now it does the same thing it did before I installed the plugin.  It says "playing" for a second, then "stopped" and stays there.  Has anyone figured out a permanent solution to this problem??

---

### Post by pclowser on 2007-08-02
I had the same problem. I found a stand-alone player here:

[http://www.xmfan.com/viewtopic.php?t=78936]("http://www.xmfan.com/viewtopic.php?t=78936")

You need to compile it, and you need the Qt4 framework installed 

```
sudo apt-get install qt4-designer
```

The player works well, but the volume control doesn't work from me. Hope this helps!

---

### Post by liquoredolce on 2007-09-10
I got the qt4 installed and the uniXM downloaded, but can't figure out how to compile or make the file.  Could someone please lend a hand?  (I'm very novice at linux, trying to learn my way around so I appreciate any help) :)

---

### Post by pclowser on 2007-09-25
There is a file in the extract called INSTALL that tells you to run:
```
qmake
make
```
You can edit XMchannel_info.cpp to update some recently changed channels -- 2 and 45, for example. The code is well documented, so you can change it without fear of breaking anything. You can always extract the file again, if needed. You need to recompile the program after making changes.

---

### Post by clblanchard on 2007-09-28
what about adding presets?  I have looked at the info.cpp and it's seems to be only for channel descriptions.

thanks for any help

---

### Post by Sabot on 2008-02-12
The best way to get xmradio.com to work is to install two packages in Synaptic.

Totem-xine
libxine1-plugins

It works with no issues.

---

