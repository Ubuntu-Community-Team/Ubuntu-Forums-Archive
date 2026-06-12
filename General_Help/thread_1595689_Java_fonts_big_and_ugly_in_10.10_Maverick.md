---
title: "Java fonts big and ugly in 10.10 Maverick"
date: 2010-10-13
forum: General Help
---

### Post by bjtuna on 2010-10-13
I upgraded from 10.04 to 10.10 yesterday and now the fonts in Java GUI apps (eg, Netbeans, screenshot below) are big and ugly. Anybody know what's going on, and/or how to fix this?  I'm using Sun Java but the same thing was happening with the default OpenJDK.

---

### Post by bjtuna on 2010-10-13
Okay, well I solved it (sorta). By default, Swing apps like Netbeans on Ubuntu want to use the GTK Look and Feel, which inherits font sizes (and other hints) from your environment's GTK configuration. On Ubuntu, that's controlled by System -> Preferences -> Appearance -> Fonts -> Application Font.

If you change Application Font from the default of 11 down to 10, the fonts within the Swing apps like Netbeans will render much more smoothly.  However, despite what anyone in the Java fantasy land will tell you, no amount of command-line switches to Netbeans will make those fonts render with subpixel smoothing. I am currently using the following in netbeans.conf:

-J-Dswing.aatext=true -J-Dawt.useSystemAAFontSettings=lcd

And it doesn't appear to change an effin' thing.  You can crow and crow about it, but I can promise you that nobody will ever acknowledge this is actually a bug, even though it is.

---

### Post by rakete on 2010-10-13
experiencing the same thing.

thinking the whole week: "For christs sake, what the heck is Oracle doing to all this nice piece of softwares!"

I presume there is a fix for paying customers sooner or later... F*#K Oracle... I take a look if eclise suffers from this, too, and maybe switching back if it is better there...

btw. I wasn't so bad a week ago... there must be an update which causes this.. maybe it's not oracles fault (but I hardly can think of this)

---

### Post by samtihen on 2010-10-13
Same issue. Just confirming.

---

### Post by rakete on 2010-10-18
I tried around a bit and it went much better with adding
```
-J-Dawt.useSystemAAFontSettings=on
```to default start parameters in netbeans.conf.

Now my default start parameters look like this (I removed some "-J-Dapple" related params from the default params. I do not recommend to do that, but I did. ;) ):
```
netbeans_default_options="-J-client -J-Xss2m -J-Xms32m -J-XX:PermSize=32m 
-J-XX:MaxPermSize=200m -J-Dsun.java2d.noddraw=true -J-Xverify:none 
-J-Dawt.useSystemAAFontSettings=on"
```instead or for other programms you can run 
```
export _JAVA_OPTIONS="-Dawt.useSystemAAFontSettings=on"
```in a terminal and start it from there or add 
```
_JAVA_OPTIONS="-Dawt.useSystemAAFontSettings=on"
```
to your "/etc/enviroment" file, but I have not tried that.

hope that helps.

Sources:
[http://hedayatvk.wordpress.com/2010/02/26/antialiasing-and-java/](http://hedayatvk.wordpress.com/2010/02/26/antialiasing-and-java/)
[http://www.linuxquestions.org/questions/linux-software-2/java-swing-anti-aliasing-610175/](http://www.linuxquestions.org/questions/linux-software-2/java-swing-anti-aliasing-610175/)

---

### Post by bjtuna on 2010-10-18
@rakete: Notice, though, that even with useSystemAAFontSettings=on, the fonts are anti-aliased but there's no subpixel smoothing; the fonts don't truly match those in the rest of your apps.  And if you try any of the other possible values for useSystemAAFontSettings, you'll notice they pretty much all have the same effect:

[http://download.oracle.com/javase/6/docs/technotes/guides/2d/flags.html#aaFonts](http://download.oracle.com/javase/6/docs/technotes/guides/2d/flags.html#aaFonts)

---

### Post by rakete on 2010-10-18
yes, that's true, but I think it always was. 
But It wasn't even antialised, it is better now for me, especially the editor text.
GUI looks kind of differnet, but it always have. Would be good to choose a smaller fontsize for netbeans GTK look and feel, but I haven't figured out how, yet...

---

### Post by TheCosmicFrog on 2010-10-19
Have this exact same issue. I've also noticed that people on the Oracle side seem to block their ears and pretend it's not happening. Fonts in Java apps look incredibly ugly. And OP's recommendation to change to size 10 for Application Font didn't make any difference.

Java version:
```

java version "1.6.0_21"
Java(TM) SE Runtime Environment (build 1.6.0_21-b06)
Java HotSpot(TM) 64-Bit Server VM (build 17.0-b16, mixed mode)

```

---

### Post by arikkfir on 2011-01-02
Yes this happens for me. A way to make all fonts in Java apps smaller would go a long way indeed. It almost seems that the metrics used by AWT/Swing are different than the standard X11 metrics.

---

### Post by marcosbdm on 2011-03-04
Same problem here.
Ubuntu 10.10, Sun Java, Netbeans 6.9

tried the different options, but sill no good font rendering.

---

### Post by bijur on 2011-04-19
+1

Me too. Have tried everything. No hope.

The "less sucking" option is to make the application font (system-wide) smaller in System->Preferences->Appearance.

This REALLY sucks :(

---

### Post by PowerKiKi on 2011-06-15
Same here with Netbeans 7.0 and Natty.

I noticed that changing the Look And Feel as described in [netbeans documentation]("http://ubuntuforums.org/com.sun.java.swing.plaf.gtk.GTKLookAndFeel") then allow you to use the --fontsize switch to [specify a custom size]("http://wiki.netbeans.org/FaqFontSize"). So it may be a bug related to com.sun.java.swing.plaf.gtk.GTKLookAndFeel[FONT=Arial]. [/FONT] But I don't like any other LAF and I don't see why I should change the whole LAF to just use a decent font size in the first place.

I ended up reducing the system wide font size to 10. "less sucking" solution FTW !

---

