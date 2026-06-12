---
title: "openfitness won't install"
date: 2006-06-11
forum: General Help
---

### Post by [LvN]N3misiS on 2006-06-11
I'm having trouble installing openfitness ( [http://www.workoutware.com/openfitness/download_files_skip.shtml](http://www.workoutware.com/openfitness/download_files_skip.shtml) )on my dapper installation. It worked find on breezey but now when I try install it in dapper:

```
chmod +x openfitness_unix_1_0_0.sh
 ./openfitness_unix_1_0_0.sh
Starting Installer ...
java.lang.IllegalArgumentException: Couldn't load image: welcome.png
   at gnu.java.awt.peer.gtk.GtkImage.<init>(lib-gnu-java-awt-peer-gtk.so.7)
   at gnu.java.awt.peer.gtk.GtkToolkit.createImage(lib-gnu-java-awt-peer-gtk.so.7)
   at gnu.java.awt.peer.gtk.GtkToolkit.getImage(lib-gnu-java-awt-peer-gtk.so.7)
   at javax.swing.ImageIcon.<init>(libgcj.so.7)
   at javax.swing.ImageIcon.<init>(libgcj.so.7)
   at com.install4j.runtime.installer.frontend.BaseScreen.getBannerIcon(Unknown Source)
   at com.install4j.runtime.installer.frontend.BaseScreen.setupComponent(Unknown Source)
   at com.install4j.runtime.installer.frontend.BaseScreen.initScreen(Unknown Source)
   at com.install4j.runtime.installer.frontend.screens.WelcomeScreen.<init>(Unknown Source)
   at com.install4j.runtime.installer.frontend.InstallerWizard.setupScreens(Unknown Source)
   at com.install4j.runtime.installer.frontend.InstallerWizard.<init>(Unknown Source)
   at com.install4j.runtime.installer.Installer.initWizard(Unknown Source)
   at com.install4j.runtime.installer.Installer.access$000(Unknown Source)
   at com.install4j.runtime.installer.Installer$1.run(Unknown Source)
   at java.awt.event.InvocationEvent.dispatch(libgcj.so.7)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.7)
   at java.awt.EventDispatchThread.run(libgcj.so.7)
java.lang.IllegalArgumentException: Couldn't load image: welcome.png
   at gnu.java.awt.peer.gtk.GtkImage.<init>(lib-gnu-java-awt-peer-gtk.so.7)
   at gnu.java.awt.peer.gtk.GtkToolkit.createImage(lib-gnu-java-awt-peer-gtk.so.7)
   at gnu.java.awt.peer.gtk.GtkToolkit.getImage(lib-gnu-java-awt-peer-gtk.so.7)
   at javax.swing.ImageIcon.<init>(libgcj.so.7)
   at javax.swing.ImageIcon.<init>(libgcj.so.7)
   at com.install4j.runtime.installer.frontend.BaseScreen.getBannerIcon(Unknown Source)
   at com.install4j.runtime.installer.frontend.BaseScreen.setupComponent(Unknown Source)
   at com.install4j.runtime.installer.frontend.BaseScreen.initScreen(Unknown Source)
   at com.install4j.runtime.installer.frontend.screens.WelcomeScreen.<init>(Unknown Source)
   at com.install4j.runtime.installer.frontend.InstallerWizard.setupScreens(Unknown Source)
   at com.install4j.runtime.installer.frontend.InstallerWizard.<init>(Unknown Source)
   at com.install4j.runtime.installer.Installer.initWizard(Unknown Source)
   at com.install4j.runtime.installer.Installer.access$000(Unknown Source)
   at com.install4j.runtime.installer.Installer$1.run(Unknown Source)
   at java.awt.event.InvocationEvent.dispatch(libgcj.so.7)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.7)
   at java.awt.EventDispatchThread.run(libgcj.so.7)

```

and i get a pop-up error

An error occurred:
java.lang.NullPointerException
Errorlog: /tmp/install4jError5ulftclog

---

### Post by taurus on 2006-06-11
It looks like it is having a problem with java!!!  Do you have java installed and which version do you have?

---

### Post by [LvN]N3misiS on 2006-06-11
I have java installed. Here is a screencap of various packages I have installed, hope it helps.
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=11081&stc=1&d=1150084648[/IMG]

---

### Post by [LvN]N3misiS on 2006-06-12
anyone got any suggestions?

---

### Post by Azurlune on 2006-06-12
You could try running *sudo update-alternatives --config java*, and making sure that the Sun java is selected as the program that provides java. If it isn't, try selecting it and then running the program again.

---

### Post by Hairy_Palms on 2006-06-12
it works fine for me, i am using sun as my default java so id guess thats your problem, its an ok program, but i think ill stick with fitday :)

---

### Post by [LvN]N3misiS on 2006-06-12
[QUOTE=Azurlune]You could try running *sudo update-alternatives --config java*, and making sure that the Sun java is selected as the program that provides java. If it isn't, try selecting it and then running the program again.[/QUOTE]


this did the trick thanks. :D

---

