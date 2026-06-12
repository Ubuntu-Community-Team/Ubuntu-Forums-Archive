---
title: "Java swing default look and feel"
date: 2012-06-20
forum: General Help
---

### Post by Zvlwab on 2012-06-20
When I run a java swing application, the metal look and feel is detected as the default one. My swing.properties file looks like this:
```
me@pc:~$ cat /etc/java-7-openjdk/swing.properties 
# uncomment to set the default look and feel to GTK
swing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel
```

Back at the time I used Gnome2 in Ubuntu 10.10, it just worked. Now since I upgraded to Xubuntu 12.04 it doesn't work anymore.
I really want to change it, because I think the metal look and feel is really ugly.

---

### Post by dr_saaron on 2012-06-20
Probably a dumb question, but what version of java are you running?  Are you using the java that's in that location?

---

### Post by Zvlwab on 2012-06-20
On my laptop I only have openjdk 7 installed. On my pc I have both 6 and 7 installed (because one program depends on 6), but 7 is the default.

---

### Post by awilkins on 2012-10-05
I'm seeing the same - I have both OpenJDK 6 and 7. Starting apps under 6 looks much nicer than 7, mostly because Java 7 has nasty looking bold fonts.

Comparing the default system properties of Java 6 and Java 7, the only related difference seems to be that Java 7 has

  ```
awt.toolkit = sun.awt.X11.XToolkit
```

Changing this value just breaks things as I can't seem to use any of the other available toolkits.

Comparing /etc/java-6 and /etc/java-7 reveals nothing useful, in particular, swing.properties files are identical (and nothing but comments).

Changing the look and feel : 

Motif : hideous and cyan

Windows : absent

GTK is the same as the System look and feel and is apparently just much uglier in Java 7 than it is in Java 6.

Metal : nicer fonts but hideous chrome.

Nimbus : dies with a NullPointerException (running JConsole)

Examining the source ; nothing obvious in "com.sun.java.swing.plaf.gtk" that would cause the GTK look and feel to have those nasty bold fonts.

So I'm stumped. Bah.

---

