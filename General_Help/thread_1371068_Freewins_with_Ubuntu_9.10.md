---
title: "Freewins with Ubuntu 9.10"
date: 2010-01-03
forum: General Help
---

### Post by tom.swartz07 on 2010-01-03
Hi all,

I know that there are a few threads here with how-to's on how to install the Compiz plugin Freewins:
[http://ubuntuforums.org/showthread.php?t=602062&highlight=freewins](http://ubuntuforums.org/showthread.php?t=602062&highlight=freewins)
etc...

Unfortunately, there seem to be some old, missing packages that are not supported. Can anyone help me sort through this pile of old material to get this plugin working?

For those who dont know what freewins does: [http://www.youtube.com/watch?v=CfCjRabPneU&feature=related](http://www.youtube.com/watch?v=CfCjRabPneU&feature=related)

Thanks!

---

### Post by aviedw on 2010-01-03
Just wondering, what function does this plug-in provide. This would be a really cool plug-in if information could be added to the back of the web page. But i dont see the reason for adding this plug in to your system. I dont mean any disrespect im just wondering why you want this particular plug-in.

---

### Post by tom.swartz07 on 2010-01-03
> **aviedw said:**
> Just wondering, what function does this plug-in provide. This would be a really cool plug-in if information could be added to the back of the web page. But i dont see the reason for adding this plug in to your system. I dont mean any disrespect im just wondering why you want this particular plug-in.

It allows you to 'turn' windows to angles; basically giving the windows a keystone effect that fools you into believing that youre spinning the window.


Just as an example, I would like to use it for windows that I keep on top of others so that they are angled out of the way. say for instance that I have Chrome open, and a small IM window on top, I would like to angle the window in such a way that i could still see parts of my browser.

Also, it just looks pretty darn cool. :D

---

### Post by tom.swartz07 on 2010-01-03
bumpy bump?

---

### Post by chewearn on 2010-01-03
Note: Freewins (Freely Transformable Windows) is classified as experimental, i.e. you break it, you keep the pieces.  I tried it long time ago, and it never worked quite right.

[http://wiki.compiz.org/Plugins/Freewins](http://wiki.compiz.org/Plugins/Freewins)

How to install:
[http://wiki.compiz.org/Install/PluginsFromGit](http://wiki.compiz.org/Install/PluginsFromGit)

---

### Post by tom.swartz07 on 2010-01-03
> **chewearn said:**
> Note: Freewins (Freely Transformable Windows) is classified as experimental, i.e. you break it, you keep the pieces.  I tried it long time ago, and it never worked quite right.

[http://wiki.compiz.org/Plugins/Freewins](http://wiki.compiz.org/Plugins/Freewins)

How to install:
[http://wiki.compiz.org/Install/PluginsFromGit](http://wiki.compiz.org/Install/PluginsFromGit)

following the directions on the installation page, it gives the error that ```
tom@ubuntu-karmic:~/compiz/freewins$ make
Makefile:48: *** [ERROR] Compiz not installed.  Stop.

```

What now? Will it just not work for the current version of Compiz?

Compiz is up to date: ```
tom@ubuntu-karmic:~/compiz/freewins$ sudo apt-get install compiz
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by chewearn on 2010-01-04
Note "Requirements" section; have you install:
*compiz-fusion-dev* (or *compiz-dev*)
*compiz-bcop* (or *bcop*)

---

### Post by hariks0 on 2010-01-04
I would rather prefer the shade/rollup feature in Ubuntu tweak.

---

### Post by Floriann on 2010-03-27
I knew compiz was installed, so I commented the compiz section in the makefile. Not very safe, but effective. Then it gave an error about cairo-xlib that wasn't installed. I fixed this one by installing libcairo2-dev (and a whole bunch of packages). But now it's giving me 

```
make: *** No rule to make target `build/util.lo', needed by `c-build-objs'.  Stop.
```

I cannot seem to fix this error. I suppose the Makefile is outdated.

---

### Post by hariks0 on 2010-03-28
I ran an installation script available at [Compiz Community Furum.]("http://forum.compiz.org/viewtopic.php?f=114&t=12012") It was very cool. The only problem with freewins is that if I click in the title bat of any window, every thing freezez. It my be my lack of knowledge as actually the keyboard is still usable. Rotation and scaling works well.

Try it and post back.:popcorn:

---

