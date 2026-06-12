---
title: "Java Error?? Maybe"
date: 2010-03-30
forum: General Help
---

### Post by cwfrad on 2010-03-30
I'm Trying to run the budget calendar from mishell.com which was a sh. file...I installed it and its in my applications.  When I click on it nothing happens, when I try running it in a terminal I get this..

[PHP]Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/local/share/Budget/platform/linux/swt/gtk/libswt-pi-gtk-3138.so: /usr/local/share/Budget/platform/linux/swt/gtk/libswt-pi-gtk-3138.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1747)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1672)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
    at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
    at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
    at Budget.main(Unknown Source)[/PHP]

---

