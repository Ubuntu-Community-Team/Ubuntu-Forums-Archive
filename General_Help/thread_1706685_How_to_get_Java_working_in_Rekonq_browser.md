---
title: "How to get Java working in Rekonq browser?"
date: 2011-03-14
forum: General Help
---

### Post by bastones on 2011-03-14
Hi,

I've tried installing Java and then symbolically linking the respective .so file to the usr/lib/mozilla/plugins folder via the Terminal but without luck. Rekonq still doesn't detect Java so I presume I need to symlink the .so file elsewhere? Unless it does need to be in the mozilla/plugins folder but I am synlinking an incorrect .so file? - though I'm following the Java.com instructions for Firefox/Mozilla. Opera detects the plugin through that folder so I'd presume Rekonq does, too?

Thanks.

---

### Post by ankspo71 on 2011-03-15
Hi,
I haven't tried Java in Rekonq, so I'm not aware of any java plugin problems, but I see you are following the instructions on the java.com site, so I think you have installed the java which you have downloaded from the java.com site. Have you already tried using Sun Java (or OpenJDK) from Ubuntu's own repositories? If this is what you are doing then you can disregard this post.

Sun Java is still available in Ubuntu, but an additional repository must be enabled in order to get it. 'sun-java6-jre' and 'sun-java6-plugin' should be available in the "partner" repositories. This applies to *ubuntu 10.10, and also 10.04 as far as I can tell.

Open Kpackagekit (Software Management), then click on settings, click on Edit Origins, click on the Other Software tab, then enable "Canonical Partners". (see screenshot below)

If for some reason you don't have those repositories listed as an option, you can add these repositories to the list by clicking on the add button.

```
For Kubuntu 10.10
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

For Kubuntu 10.04
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
```

Now click on the close button and reload/refresh your repositories when prompted. Now you can search for sun-java6 to find the packages you need.

Hope this helps.

PS. 'openjdk-6-jre' and 'icedtea6-plugin' are open-source alternatives to 'sun-java6-jre' and 'sun-java6-plugin'.

---

### Post by lykeion on 2011-03-15
It seems that Java plugin support in Rekonq (using the Qt port of WebKit) is still under development, see
[http://mail.kde.org/pipermail/rekonq/2010-October/001704.html](http://mail.kde.org/pipermail/rekonq/2010-October/001704.html)

I don't know but I suspect the Qt development is halted because of Nokia's move towards Windows Phone platform and their decision to let Digia acquire Qt commercial licensing business.

---

