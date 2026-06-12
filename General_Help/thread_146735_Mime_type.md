---
title: "Mime type"
date: 2006-03-18
forum: General Help
---

### Post by GregaS on 2006-03-18
I get this error message every time I start application:

[img]http://www2.shrani.si/files/mime2343334.png[/img]

How do I get rid of it?

---

### Post by ltmon on 2006-03-18
That sounds like something is missing, although it shouldn't be in a standard installation.

Can you tell my if this file exists:
```

/usr/share/mimelnk/application/octet-stream.desktop

```

If it is there, try the following in a terminal:
```

kbuildsycoca

```
then try again.

If it isn't there do the following:
```

sudo apt-get install --reinstall kdelibs-data

```
and see if it helps.

Cheers,

L.

---

### Post by GregaS on 2006-03-19
octet-stream.desktop file exist but when I enter kbuildycoca I get this:

> Warning: kbuildsycoca is unable to register with DCOP.
kbuildsycoca running...
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!

---

### Post by Barrakketh on 2006-03-19
Here's something to try:

[list][*]Log out of KDE
[*]Press Ctrl+Alt+F2 and log in under your account.
[*]Do the following:
```
rm /var/tmp/kdecache-$USER/ksycoca
```
[*]Log out and and switch back to KDM (Ctrl+Alt+F7)
[*]Log back in to KDE and see if that fixes your problem.  If that fails, repeat the previous steps except for the command you run, which should be:
```
rm -f /var/tmp/kdecache-$USER
```[/list]

If you haven't figured it out yet, replace $user with your user name :)

---

### Post by GregaS on 2006-03-19
Thanks for your help. I saw that many people had the same problem as I had. Here is fix to the problem: [http://users.pandora.be/Ice9/Linux%20stuff/Linux_tips.html](http://users.pandora.be/Ice9/Linux%20stuff/Linux_tips.html)

---

