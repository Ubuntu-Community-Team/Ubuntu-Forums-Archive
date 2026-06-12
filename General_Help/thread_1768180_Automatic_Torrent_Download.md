---
title: "Automatic Torrent Download"
date: 2011-05-26
forum: General Help
---

### Post by Kissell on 2011-05-26
Is anyone able to get torrents to automatically download from an RSS feed or other method in Ubuntu?  Certainly someone is doing this somewhere, but I cannot figure out any method that works in Ubuntu, so currently I have to have a 2nd box, a microsoft machine (gasp) running 24/7 just for this purpose, because I can't figure it out in linux.

On windows I use RSS feeds inside a bittorrent client, but none of the clients I find in linux support RSS feeds, except Deluge, which is at first a beautiful client until you actually use it and find out it is a horrible program that crashes and freezes more often than it works.

I have heard about TED, an automatic torrent downloader, but I can't get the latest version from their website to install on 11.04, I get some java errors when I try to open the .jar file.

> # java ted.jar
Exception in thread "main" java.lang.NoClassDefFoundError: ted/jar
Caused by: java.lang.ClassNotFoundException: ted.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: ted.jar. Program will exit.


I don't care if I use ted or a bittorrent client with rss feed capability, as long as it works.  And since deluge crashes and ted won't load, I'm lost.  Anyone using anything else to accomplish this?

---

### Post by Kissell on 2011-05-26
Well, I hadn't tried Deluge in a long time, so I gave it a try again, and it doesn't come with an RSS plugin.  I could only find one, but couldn't get it to show up in the GUI when I added the egg file.

So I tried Wine with the uTorrent client I am using in windows...  that actually seems to work well so far...  I'll give that a shot and see if it works out.

---

