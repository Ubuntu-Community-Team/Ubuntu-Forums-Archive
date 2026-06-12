---
title: "Java Runtime Environment won't work in firefox"
date: 2006-06-16
forum: General Help
---

### Post by UbuntuniX on 2006-06-16
Well JRE appears to be installed in my ubuntu partition,
if I enter java -version in terminal I get this output:

```

java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

But in firefox if I type about:plugins it says none are installed.

Is there any way to get it into firefox?

---

### Post by Rui Pais on 2006-06-16
hi,
do you have any link at .mozilla/plugins/ directory to a libjavaplugin_oji.so file?

If not, do:
```
slocate libjavaplugin_oji.so
```
should give something like:
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
or
/usr/local/j2re1.4.2_05/plugin/i386/ns610/libjavaplugin_oji.so

Link the path to there, should be something like:
```
ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/libjavaplugin_oji.so
```

Note, It must be a symlink not a copy of the file, or it wont work.

hth.

---

### Post by FadedEidolon on 2006-06-17
I have been unable to locate a "libjavaplugin_oji.so".  The nearest file I've found is a "libjawt[something].so"  Any ideas?

---

### Post by Poka64 on 2006-06-17
Try to install sun-java5-plugin through synaptic

---

### Post by Braim on 2006-06-17
Try this 

```

sudo apt-get install sun-java5-jre sun-java5-fonts sun-java5-plugin
sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```

It should work but maybe... you'll need an extra repository. I can't remeber wich one it is :rolleyes:

---

### Post by Rui Pais on 2006-06-17
hi, libjavaplugin_oji.so is part of sun-java5-bin:
```
dpkg -S libjavaplugin_oji.so
sun-java5-bin: /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
sun-java5-bin: /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
```

---

### Post by FadedEidolon on 2006-06-18
Got it!  Thanks!

---

### Post by s_g_robertson on 2007-12-05
> **Rui Pais said:**
> hi,
do you have any link at .mozilla/plugins/ directory to a libjavaplugin_oji.so file?

If not, do:
```
slocate libjavaplugin_oji.so
```
should give something like:
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
or
/usr/local/j2re1.4.2_05/plugin/i386/ns610/libjavaplugin_oji.so

Link the path to there, should be something like:
```
ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/libjavaplugin_oji.so
```

Note, It must be a symlink not a copy of the file, or it wont work.

hth.

I know this is an old thread but...

I found this and this fixed my problem without any problems, but I am just wondering if anyone has any ideas why this step is necessary.  Is/was this always required or did something not work with my installation of java?

Thanks
Stephen.

---

