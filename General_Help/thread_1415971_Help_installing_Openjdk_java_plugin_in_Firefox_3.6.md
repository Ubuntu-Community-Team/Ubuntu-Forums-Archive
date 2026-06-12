---
title: "Help installing Openjdk java plugin in Firefox 3.6 in 9.10"
date: 2010-02-25
forum: General Help
---

### Post by auh2o on 2010-02-25
I've installed openjdk-6-jre via Synaptic, and created what I would have thought were the necessary symlinks to
```

/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
```in the Firefox plugin directories:

```
/usr/lib/firefox/plugins/
/usr/lib/mozilla/plugins/
/etc/alternatives/firefox-javaplugin.so
/etc/alternatives/mozilla-javaplugin.so
/opt/firefox/plugins
``` (I'm using the Mozilla build from the Ubuntuzilla repo)

But I still can't get java to work. about:plugins doesn't show a trace of Java after restarting.
I even tried deleting xpti.dat in my Firefox profile directory to let it rebuild.

What am I doing wrong?

---

### Post by nanotube on 2010-02-25
well, either you're not linking to the right .so library... or openjdk doesn't come with a library using the new plugin interface. (as in, sun jre has a libjavaplugin_oji.so, which uses an old plugin interface that ff3.6 doesn't recognize, and a libnpjp2.so, which works with ff3.6... maybe there's a similar deal in openjdk)

at any rate - any particular reason you're using openjdk instead of sun jre? they're both in the official ubuntu repos, you know...

---

### Post by auh2o on 2010-02-26
[QUOTE=nanotube]at any rate - any particular reason you're using openjdk instead of sun  jre? they're both in the official ubuntu repos, you know...     [/QUOTE]

The main reason:

> [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

OpenJDK and the  Icedtea Plugin are fine for most people. There's only an outdated and  insecure version of Sun Java Runtime Environment (JRE) available in the  software sources of Ubuntu 9.10 Karmic Koala. This version won't be  updated and will possibly even be removed entirely. 

The reason:  it's open source brother OpenJDK (and the IcedTea plugin) is a good  alternative, for most people at least. 

OpenJDK and the IcedTea  plugin are available in the normal Ubuntu repositories and receive  regular security updates.Sure, I could download the latest bin of Sun Java, but why bother? Sun is virtually completely merging the two in the next version anyway. And at any rate, I'd still have to make the correct symlinks after installation.

So I might be linking the wrong so-library? Or is there no OpenJDK support for Firefox 3.6 yet?

OR, I just got to thinking, do I have to install icedtea6-plugin? That doesn't make much sense to me, since IcedTea is a Redhat fork of OpenJDK with 100% FOSS, and not an addon to the OpenJDK package, am I right? If there is a working Firefox plugin, shouldn't it already have been installed with OpenJDK?

I'm lost. If anybody could tell me the name of the correct so-library and where to find it, I'd appreciate it.

---

