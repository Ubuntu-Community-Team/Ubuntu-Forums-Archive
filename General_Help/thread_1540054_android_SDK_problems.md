---
title: "android SDK problems"
date: 2010-07-27
forum: General Help
---

### Post by zbeekman on 2010-07-27
Hi, I am having some minor issues with the android SDK.  Specifically in the tools directory of the sdk if i try to run the command android without any arguments to launch the GUI SDK and AVD manager I get the following error:


```
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-gtk-3550 or swt-gtk in swt.library.path, java.library.path or the jar file
	at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
	at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
	at org.eclipse.swt.internal.C.<clinit>(Unknown Source)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
	at org.eclipse.swt.widgets.Display.<clinit>(Unknown Source)
	at com.android.sdkmanager.Main.showMainWindow(Main.java:265)
	at com.android.sdkmanager.Main.doAction(Main.java:249)
	at com.android.sdkmanager.Main.run(Main.java:94)
	at com.android.sdkmanager.Main.main(Main.java:83)
```

the command ```
android list
``` seems to work fine, and I have installed Eclipse 3.5 and the ADT plugin and I can launch the android SDK and AVD manager from there without problems.  I am running Lucid (10.04) on an i686 Thinkpad T60.  I have installed both sun-java6-jdk and openjdk6 and tried switching between them but still no dice.

---

### Post by dionblundell on 2011-07-29
Did you ever solve this? I had the same issue 12 months on. I discovered that it was because I had made the /tmp directory "noexec" as soon as I made it executable, we were fine.```
sudo mount -o remount,exec /tmp
```Hope this helps someone.

---

### Post by brandyn on 2011-12-18
> **dionblundell said:**
> Did you ever solve this? I had the same issue 12 months on. I discovered that it was because I had made the /tmp directory "noexec" as soon as I made it executable, we were fine.```
sudo mount -o remount,exec /tmp
```Hope this helps someone.

YES!  Thank you!  (How on earth did you figure this one out???)

Been scratching my head over this all day 'til I found your lone little note.  Fixed the problem immediately.  (Kubuntu with tmpfs /tmp noexec..)

---

### Post by mondechris on 2013-01-30
Thank you!!!!
How on earth did you figure it???
Anyway thanks!!!!!!:D

---

