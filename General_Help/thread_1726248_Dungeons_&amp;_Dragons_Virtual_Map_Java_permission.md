---
title: "Dungeons &amp; Dragons Virtual Map Java permission denied."
date: 2011-04-10
forum: General Help
---

### Post by brigadoon on 2011-04-10
Hello all,

I am currently helping out (aka volunteered) with beta testing the new Dungeons & Dragons Virtual Table. This is a Java based web application that works well with Windows XP. It does not load with Ubuntu 10.10 unfortunately. My application notes for this challenge can be found at...

[http://community.wizards.com/dndbeta/go/thread/view/116549/27431553/Virtual_Map_does_not_work_with_Ubuntu_10.10_native_andor_Wine_1.3](http://community.wizards.com/dndbeta/go/thread/view/116549/27431553/Virtual_Map_does_not_work_with_Ubuntu_10.10_native_andor_Wine_1.3)

To make a long story short Java (openjdk-6 and sun-java6) is denied permission for two modules. The verbose error message is as follows...

[B]Requesting permission: (java.lang.RuntimePermission accessClassInPackage.sun.security.internal.spec)
Denying permission: (java.lang.RuntimePermission accessClassInPackage.sun.security.internal.spec)
Requesting permission: (java.lang.RuntimePermission accessClassInPackage.sun.security.internal.spec)
Denying permission: (java.lang.RuntimePermission accessClassInPackage.sun.security.internal.spec)
SM: app: DnD  is adding a window:  javax.swing.JDialog[dialog1,0,0,0x0,invalid,null,  defaultCloseOperation=DO_NOTHING_ON_CLOSE,  rootPane=,rootPaneCheckingEnabled=false]
[/B]

The Virtual Table has integrated voice over IP provided by Vivox Voice Systems. There is also a remote access worked into it. I believe that they are being denied permission by Ubuntu. Does anyone know of a way to over-ride the permissions temporarily or how to provide access for these applications?

The Virtual Table lets people from anywhere play a game of D&D together over the internet as if they were seated around the same table. The table seems to be compatible with all released editions of D&D and is a very cool idea.

---

### Post by brigadoon on 2011-04-11
bump

---

