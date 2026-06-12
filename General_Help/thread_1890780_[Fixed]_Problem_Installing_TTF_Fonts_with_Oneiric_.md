---
title: "[Fixed] Problem Installing TTF Fonts with Oneiric (11.10)"
date: 2011-12-04
forum: General Help
---

### Post by ytene on 2011-12-04
Today I tried to add some old TTF files that I have used in some of my [now very old] documents - files that were originally written in Word for Windows and are now maintained with LibreOffice Writer. Using KDE (not kubuntu, but KDE installed on top of ubuntu 11.10 - long story, don't ask!) I repeatedly got a weird and never-before-seen error message during the "font add" step. 

Basically, there are 2 error messages issued by this applet: one is the generic "you already have this file installed" message, to which the correct response is usually "skip"; the second was new to me, and basically it gave a warning that "Authentication Failed" but without telling me what Authentication or why. 

At first I suspected some weird legacy DRM, but this proved to not be the case. Various failed attempts [i.e. manually putting ttf files into the /usr/share/fonts/truetype/ folder structure] aside, I eventually found the following status messages written to /var/log/syslog:-

Dec  4 11:59:30 voyager kernel: [ 1204.865775] r8169 0000:03:00.0: eth0: link up
[B]Dec  4 12:01:17 voyager dbus[1145]: [system] Activating service name='org.kde.fontinst' (using servicehelper)
Dec  4 12:01:17 voyager dbus[1145]: [system] Successfully activated service 'org.kde.fontinst'[/B]
Dec  4 12:01:36 voyager kernel: [ 1330.517048] r8169 0000:03:00.0: eth0: link up

That got me thinking about whether or not I needed root permission to actually make changes to system font files, so searched for that, finding useful clues in a knoppix thread on the kde web site (here, for those interested):

[http://forum.kde.org/viewtopic.php?f=202&t=91646&start=15](http://forum.kde.org/viewtopic.php?f=202&t=91646&start=15)

... that there were aspects of security wrapped into administrative actions that operate at a KDE level. I spent a little time in a failed attempt to add a new version of the Menu option to invoke "systemsettings" by using the KDE Menu Editor [must go back and try that again] but in the end established that

**kdesudo systemsettings -caption "%c"**

typed from the command line seemed to work just fine. Please note that I was not sure of the significance of "-caption "%c" and the "--help" for systemsettings does not offer any clues. I can only report that the above command works without any observed side effects. 

Once the system settings application opens in a sudo wrapper (with root privilege) it is possible to add any fonts that you wish to your KDE environment. It may be that this entire side adventure could have been solved by an amended version of the KDEMenu invocation command line, including "kdesudo", but I didn't get that far. If I continue to experiment and clarify this, I'll post an amendment to this thread. 

Offered in the hope that this will be useful, and in the further hope that someone in the ubuntu community could take a look with a view to implementing a permanent fix.

One more side note. If you have also been experimenting with this, and like me tried to manually add fonts into your /usr/share... folder structure, note that you **must** remove all of those files before you run the correct systemsettings approach described here. If you fail to do that, any files that you manually added to your system's font library will still not be added. To fix this, manually remove the files that you put in the /usr/share/... folder[s] and re-run the "kdesudo systemsettings" portion. I had to do this, and everything recovered just fine.

All the Best to One and All...

C

---

### Post by ytene on 2011-12-04
OK, so the above issue is clearly a regression test failure, but I am curious as to where the gap lies...

Does this exist thanks to changes made by the KDE Team in a recent release, or is this about the ubuntu implementation of KDE? If the latter, does the kubuntu build have the same issue? If not, could I have possibly done something wrong when I added my KDE packages to the basic Oneiric build?

I have my own set of regression tests that I perform each time I move to a new release of ubuntu, with focus primarily on services rather than applications [which are easier to carry over between releases]. I am now going to expand my regression testing to cover basic functions across core applications and utilities, but this just strikes me as a bit of an obvious bug... Is there something we can/should be doing with our testing cycles? 

[Bear in mind I no *nothing* about the ubuntu testing methodology..., but am just curious].

---

