---
title: "Anybody using Android notifier desktop client?"
date: 2010-09-08
forum: General Help
---

### Post by madu on 2010-09-08
Hi,

Today I read about the Android notifier for desktop ([http://code.google.com/p/android-notifier/](http://code.google.com/p/android-notifier/)) and wanted to try it on my Ubuntu with my Android. The desktop client for Linux is here:[http://code.google.com/p/android-notifier-desktop/](http://code.google.com/p/android-notifier-desktop/)

Unfortuntely the sektop client is not working. When I start the app, I get an error notifications saying "Failed to bind to:0.0.0.0/0.0.0.0:10600".

Anybody got any idea about this?
Thank you.

---

### Post by DrDoxy on 2010-09-12
Hi,

You have to configure it first and tell the desktop client which IP address it has to use. 
See the following link for a small but clear tutorial:

[http://www.androidcentral.com/remote-notifier-android-forward-notifications-your-phone-your-computer](http://www.androidcentral.com/remote-notifier-android-forward-notifications-your-phone-your-computer)

It is aimed at Windows users, but the desktop preferences menu looks the same in Ubuntu. Only problem is that when I configure the app to startup at login, it asks me to use the system startup manager. I haven't got around that one, yet. 

Don't forget to forward port 10600 in your router.

Regards.

---

### Post by DrDoxy on 2010-09-12
Hi,

You have to configure it first and tell the desktop client which IP address it has to use. 
See the following link for a small but clear tutorial:

[http://www.androidcentral.com/remote-notifier-android-forward-notifications-your-phone-your-computer](http://www.androidcentral.com/remote-notifier-android-forward-notifications-your-phone-your-computer)

It is aimed at Windows users, but the desktop preferences menu looks the same in Ubuntu. Only problem is that when I configure the app to startup at login, it asks me to use the system startup manager. I haven't got around that one, yet. 

Don't forget to forward port 10600 in your router.

Regards.

---

### Post by madu on 2010-09-12
Thank you DrDoxy.

But how do I configure?
Is there a separate application to do the configurations? 
I even tried running from console /usr/share/android-desktop-notifier/run.sh

Still gave me the same error. 

Thank you.

---

### Post by E@zyVG on 2011-02-19
Downloaded the latest x64 version from the site. When I run it I get "Could not load UI. Make sure you are using the correct version ...."

```


vg@subnote-nix:~$ /usr/share/android-notifier-desktop/run.sh 
2011-02-19 16:50:15,443 INFO [ApplicationImpl] - Starting SWT
2011-02-19 16:50:15,557 ERROR [ApplicationImpl] - Error starting SWT
java.lang.UnsatisfiedLinkError: Cannot load 64-bit SWT libraries on 32-bit JVM
	at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
	at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
	at org.eclipse.swt.internal.C.<clinit>(Unknown Source)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
	at org.eclipse.swt.widgets.Display.<clinit>(Unknown Source)
	at com.notifier.desktop.app.SwtManagerImpl.start(SwtManagerImpl.java:44)
	at com.notifier.desktop.app.ApplicationImpl.start(ApplicationImpl.java:69)
	at com.notifier.desktop.Main.main(Main.java:106)

```

Have both 32 and 64 bit Java installed.

---

