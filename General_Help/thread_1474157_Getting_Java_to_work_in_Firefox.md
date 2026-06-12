---
title: "Getting Java to work in Firefox"
date: 2010-05-05
forum: General Help
---

### Post by Gannin on 2010-05-05
Right now I'm running Firefox 3.6.4.  In ~/.mozilla/plugins I have a link to the Java plugin.  I'm using Java version 6 update 20.

For some reason, Firefox will not acknowledge that I have the Java plugin installed.  It won't show up under Add-ons > Plugins, and if I go to a web page that requires Java, it says I don't have it installed.

I've even moved my ~/.mozilla/firefox directory, allowing Firefox to create a new empty preferences directory, and Java still won't show up.

However, Java shows up just fine in Firefox 3.5.  How do I get Java enabled?  Thanks.

---

### Post by lovinglinux on 2010-05-06
[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by Gannin on 2010-05-06
The ultimate problem was the java/jre/plugin/i386/ns7/libjavaplugin_oji.so plugin no longer works with Firefox.  The new plugin is java/jre/lib/i386/libnpjp2.so, which isn't very intuitively named or located, but there you go.

---

### Post by QIII on 2010-05-06
[FONT=Arial][SIZE=2]If you are running Lucid, look at posts 6 and 7 here:

[http://ubuntuforums.org/showthread.php?t=1467554](http://ubuntuforums.org/showthread.php?t=1467554)

Then, to make Sun Java the default:

```
sudo update-java-alternatives -s java-6-sun
```

(lovinglinux' source is good, and you can do it that way.  That's the way I used to do it.  But Java is also now in the partner repository.)
[/SIZE][/FONT]

---

### Post by docomo on 2010-05-16
Run this:

```
sudo update-alternatives --config mozilla-javaplugin.so
```

If the Java plugin in Firefox is not working then libjavaplugin_oji.so is probably selected. That plugin apparently doesn't work with Firefox 3.6. Change it to the IcedTeaPlugin or to libnpjp2.so if you want to use Sun's Java.

Also, if you are using Sun's Java, it is probably a good idea to enable the partner repository if you haven't already:

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```

---

