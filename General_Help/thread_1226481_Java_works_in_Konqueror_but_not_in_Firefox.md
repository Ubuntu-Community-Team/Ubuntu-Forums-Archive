---
title: "Java works in Konqueror but not in Firefox"
date: 2009-07-29
forum: General Help
---

### Post by mcslave on 2009-07-29
The Java Runtime Environment works in Konqueror but not in Firefox. I've tried reinstalling both the JRE package and the Firefox package. I've also tried enabling and disabling Java and Javascript in Firefox. Anyone know what I can do to get it to work?

---

### Post by Zorael on 2009-07-29
Is this Sun's Java or OpenJDK? I think that Firefox 3.5+ currently doesn't work with OpenJDK's browser plugin (**icedtea6-plugin**), and the solution is currently to "install Sun's".

Sun's browser plugin is included in the main sun-java6-bin package, so if you have the JRE, you have it installed. However, it doesn't "install" itself as a Mozilla plugin unless you install the **sun-java6-plugin** package. So, make sure it's installed. If it is and it still doesn't work, reconfigure the package to let it reassert itself.
```
$ sudo dpkg-reconfigure sun-java6-plugin
```
Also, check **about:plugins** in Firefox to make sure it's not listed there and you're just experiencing a Firefox bug. (The one previously mentioned is the one where you get a grey box and 100% cpu use, but no applets.)

Have a look at **/usr/lib/mozilla/plugins/**. There should be a symbolic link there - something in lieu of **libjavaplugin.so** that points to **/etc/alternatives/mozilla-javaplugin.so** which in turn points to **/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so**. You can verify that either in a terminal or via Dolphin/Konqueror. This is the link that the sun-java6-plugin package sets up.

As a small note, the route the symlinks take differs between releases (read: version of the sun-java6-plugin installer script), but there *needs* to be a link in that plugins/ directory that *eventually* ends up at **/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so**, or it won't work. To further confusion, the filename is different if you're on a 64-bit installation. But the plugin package should take care of that.

If you don't trust it to set up the link for you, you could do it yourself.
```
$ sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/libjavaplugin.so
```

[Then test it here](http://javatester.org).

---

### Post by mcslave on 2009-07-29
The plugin is now installed and Firefox restarted, but JavaScript is still not working. About:plugins shows that the Java plugin is installed as follows:

**Java(TM) Plug-in 1.6.0_14**

 File name:  libnpjp2.so The next generation [Java]("http://java.sun.com/") plug-in for Mozilla browsers.   MIME Type Description Suffixes Enabled    application/x-java-vm Java&#8482; Plug-in 
Yes   application/x-java-applet Java&#8482; Plug-in Applet 
Yes   application/x-java-applet;version=1.1 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.1.1 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.1.2 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.1.3 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.2 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.2.1 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.2.2 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.3 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.3.1 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.4 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.4.1 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.4.2 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.5 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.6 Java&#8482; Plug-in 
Yes   application/x-java-applet;jpi-version=1.6.0_14 Java&#8482; Plug-in 
Yes   application/x-java-bean Java&#8482; Plug-in JavaBeans 
Yes   application/x-java-bean;version=1.1 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.1.1 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.1.2 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.1.3 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.2 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.2.1 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.2.2 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.3 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.3.1 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.4 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.4.1 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.4.2 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.5 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.6 Java&#8482; Plug-in 
Yes   application/x-java-bean;jpi-version=1.6.0_14 Java&#8482; Plug-in 
Yes

The sym links are also all there.

---

### Post by Zorael on 2009-07-30
The plugin is irrelevant for Java**Script**. Do Java applets work now?

As for JavaScript not working, I don't have the slightest idea what could cause that, as Firefox has its own JavaScript engine built-in. Perhaps double-check that you didn't leave it disabled (you mentioned toggling it earlier).

---

### Post by mcslave on 2009-07-30
Oh, hmmm, I thought Java was responsible for that. My bad.

Anyways, I'm on the Java test page and it reports that Java is not working. I made sure that both Java and JavaScript are enabled.

---

### Post by mcslave on 2009-07-30
It's not working in Konqueror now either. Maybe try downgrading to JRE 5? It's important I get this working tonight, I need a Java applet to complete a school assignment.

---

### Post by mcslave on 2009-07-30
Ok, this is odd... on the Java test page the applet works in Konqueror. But when I go to the assignment it reports that I don't have the Java plugin installed. The test applet doesn't work in Firefox at all.

---

### Post by mcslave on 2009-07-30
I got it fixed. First I downgraded to the JRE 5 package and plugin and ensured they were working. Then I upgraded to JRE 6 and the plugin and it's working! :) Thanks for your efforts. I don't know why this worked when uninstallation and reinstallation didn't, but it's at least something to consider in the future if a simple uninstall/reinstall isn't working.

---

