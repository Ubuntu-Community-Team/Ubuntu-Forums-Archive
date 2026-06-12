---
title: "How to get a java plugin manually installed in Firefox?"
date: 2011-07-21
forum: General Help
---

### Post by leegold on 2011-07-21
Hi, using Xubuntu 11.04

I don't like Firefox 4 and 5 so I uninstalled it and installed FF 3.6.19  manually in the /opt directory. It works really well. I wanted to add a java icedtea plugin to FF. But I can't use Synaptics. Synaptics does not see the FF 3.6.19 - it does not know it's there and will try an install FF5 if I use it to install that plugin - makes sense it would do that.

How do I get a java plugin installed considering how FF is implemented on my system?

I can download a deb installer for the plugin and use the archive manager to get manually get files out of it but what I've tried so far didn't work...

Thanks,

Lee G.

---

### Post by wildmanne39 on 2011-07-21
Hi, this should do it and you will have to accept the agreement by using the arrow keys and then hit enter.
```
sudo apt-get install openjdk-6-jdk openjdk-6-jre
```

---

### Post by leegold on 2011-07-21
Well, I used Synaptic to install the open JDK and it also installs the automatically jre when the jdk is installed. So I'm not sure that's the fix. I'm pretty convinced that it has to be done manually - Synaptic doesn't "see" FF in /opt.

---

### Post by gandaran on 2011-07-21
> **leegold said:**
> Well, I used Synaptic to install the open JDK and it also installs the automatically jre when the jdk is installed. So I'm not sure that's the fix. I'm pretty convinced that it has to be done manually - Synaptic doesn't "see" FF in /opt.
that is very easy, find the icedtea6 plugin file then just copy the same file to firefox 3.6 plugins folder.
I don't use the icedtea6 plugin as I have the sun-java6-plugin installed so if I wanted the sun plugin in firefox 3.6 I would just copy the /usr/lib/mozilla/plugins/libjavaplugin.so to firefox 3.6 plugins folder.

---

### Post by lovinglinux on 2011-07-21
> **gandaran said:**
> that is very easy, find the icedtea6 plugin file then just copy the same file to firefox 3.6 plugins folder.
I don't use the icedtea6 plugin as I have the sun-java6-plugin installed so if I wanted the sun plugin in firefox 3.6 I would just copy the /usr/lib/mozilla/plugins/libjavaplugin.so to firefox 3.6 plugins folder.

Instead of manually copying plugins, just create a symlink from your system plugins folder to the opt installation.

```
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
```

You can install plugins via Synaptic as usual.

---

