---
title: "Aria 2 plugin Uget downloader"
date: 2011-09-03
forum: General Help
---

### Post by Ikmal2129 on 2011-09-03
hye.
how can i enabled aria 2 plugin on uget?
i enabled on setting but when i try to download something their error and he say aria 2 error.
how can i solved it?
BTW i install aria 2 plugin using command sudo apt-get install aria2.
but the same result.
sory for my bad english

---

### Post by Jose Catre-Vandis on 2011-09-03
Did you check the settings - paths etc

[http://uget.visuex.com/screenshots/screenshots/settings/uget-settings-plugin-10#joomimg](http://uget.visuex.com/screenshots/screenshots/settings/uget-settings-plugin-10#joomimg)

and wait for all downloads to finish as instructed?

What is the aria 2 error?

Try running a download directly through aria 2 to check it is working

---

### Post by Ikmal2129 on 2011-09-03
i have enabled the plug in.
and same error.
btw this is a photo.
read ad the message at bottom.

---

### Post by Ikmal2129 on 2011-09-03
i want aria 2 plugin because aria 2 plugin support 20 connection per server same like IDM on window.

---

### Post by Jose Catre-Vandis on 2011-09-04
I would guess that uget is looking for a specific version of aria2 and not finding it!

Also for v 1.7.6 there are some notes about aria2

> Some features will not work if you use aria2 plug-in with aria2 <= 1.9.
If you get message &#8220;aria2.getVersion failed&#8221;, it mean uget can&#8217;t connect to aria2 through XML-RPC.
make sure that your aria2 enable XML-RPC in compiling time and check network configuration.

So it looks like you will need to compile aria2 from source to get it to work. Looks like this version has XML-RPC support built in

[http://sourceforge.net/projects/aria2/files/stable/aria2-1.12.1/](http://sourceforge.net/projects/aria2/files/stable/aria2-1.12.1/)

---

### Post by acidspoof on 2012-06-20
-x 8 -k 1M --enable-rpc --rpc-listen-all=true --rpc-allow-origin-all


x is the number of connections
k is fragment size of file

---

