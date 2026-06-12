---
title: "Oracle Java 1.7 issue"
date: 2012-06-02
forum: General Help
---

### Post by jdunn on 2012-06-02
I removed Open-jdk from Ubuntu 12.04 and replaced it with an install of Oracle jdk 1.7.04 direct from Oracle's website.  It works great, except for one minor annoying problem:  Many Java apps, including Netbeans, that use the system look&feel have dark menu-text that is barely readable on Ubuntu's Ambiance theme.  To show exactly what I mean, included is a screenshot of the Netbeans opening screen.  Is anyone else having this problem and does anyone know a solution?

---

### Post by jdunn on 2012-06-17
**bump**

same problem with Oracle Java 1.7.0_05

---

### Post by Cheesemill on 2012-06-17
You could try this fix:

[https://wiki.archlinux.org/index.php/Netbeans#GTK_look_and_feel](https://wiki.archlinux.org/index.php/Netbeans#GTK_look_and_feel)

---

### Post by jdunn on 2012-06-17
Thank you, CheeseMill.  This works for NetBeans but does not take care of the problem for other Java apps that I use such as JBidWatcher and GroovyConsole.  They do not have command-line arguments for changing the theme.  I was looking for something in Ubuntu to fix the overall problem.

---

### Post by Cheesemill on 2012-06-17
Try adding this line to your ~/.bashrc
```
export _JAVA_OPTIONS=-Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel
```

From:
[https://wiki.archlinux.org/index.php/Java#GTK_LookAndFeel](https://wiki.archlinux.org/index.php/Java#GTK_LookAndFeel)

---

### Post by charlie cat on 2012-06-17
Alternatively, you can add the line:
```
swing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel
```to the file /usr/lib/jvm/java-7-sun/jre/lib/swing.properties  .
See [http://docs.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html#properties](http://docs.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html#properties) .
I think, though, that Cheesemill's method will have a better chance of surviving updates.

---

### Post by jdunn on 2012-06-20
No effect

---

