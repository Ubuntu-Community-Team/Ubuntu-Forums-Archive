---
title: "HowTo: Firefox v3.6 , Google Chrome , and java"
date: 2010-01-21
forum: General Help
---

### Post by luigi_mb on 2010-01-21
I installed Firefox v3.6 by simply downloading "firefox-3.6.tar.bz2" from the Mozilla site. I unpacked it in my home folder and launched it

```

$ cd ~
$ tar xvf firefox-3.6.tar.bz2
$ cd firefox
$ ./firefox

```

One thing that did not work was the java plugin. By googling around I found out that the usual library "libjavaplugin_oji.so" is not recognized by the new Firefox, and that one should use "libnpjp2.so" instead. As far as I know, the latter is not present in the latest jre (jre-6u18-linux-i586.bin), but is present in the jdk (jdk-6u18-linux-i586.bin). I created therefore a symlink to "libnpjp2.so"

```

ln -s /opt/java/jdk1.6.0_18/jre/lib/i386/libnpjp2.so  /home/luigi/firefox/plugins/libnpjp2.so

```

Since this procedure was successful, I tried it with Google Chrome v4.0.295.0 unstable

```

$ sudo ln -s /opt/java/jdk1.6.0_18/jre/lib/i386/libnpjp2.so /opt/google/chrome/plugins/libnpjp2.so

```

It works!


/luigi

---

### Post by nanotube on 2010-01-21
the java detection problem is actually this bug:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727)

you can install sun-java6-plugin package, then use the workaround from the bug to fix java detection. no need to install the jdk.

and while i'm here, i'll also suggest the ubuntuzilla repository as a better method of installing the latest mozilla release, than the manual extraction:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by luigi_mb on 2010-01-22
> **nanotube said:**
> the java detection problem is actually this bug:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727)

you can install sun-java6-plugin package, then use the workaround from the bug to fix java detection. no need to install the jdk.

I do need the jdk for java compilation.

> **nanotube said:**
> and while i'm here, i'll also suggest the ubuntuzilla repository as a better method of installing the latest mozilla release, than the manual extraction:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

I had bad experiences with ubuntuzilla in the past, under Ubuntu v8.04. One advantage of "manual extraction" is that it is as simple as it gets, and that I can update Firefox from Help > Check for updates. In fact on another machine I did just that, and updated v3.5.7 to 3.6.

/luigi

---

### Post by nanotube on 2010-01-23
> **luigi_mb said:**
> 
I had bad experiences with ubuntuzilla in the past, under Ubuntu v8.04. One advantage of "manual extraction" is that it is as simple as it gets, and that I can update Firefox from Help > Check for updates. In fact on another machine I did just that, and updated v3.5.7 to 3.6.


back in those days ubuntuzilla was an installer script, now it's a ppa repository, so should be cleaner and more foolproof... that said, if manual works for you, no need to mess with it. :)

---

