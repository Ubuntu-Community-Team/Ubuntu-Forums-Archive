---
title: "Korganizer won't start after upgrade"
date: 2009-12-28
forum: General Help
---

### Post by mithras86 on 2009-12-28
Hi all,
After a simple upgrade with apt, my Korganizer app doesn't start anymore. The only output from the terminal available is:
```
~$ korganizer
<unknown program name>(3157)/: Communication problem with  "korganizer" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "
~$
```
Something is definitly wrong, but how am I able to fix this? It's the same for Kontact (but that has a Korganizer part).

Thanks for any help!!! (Atm I miss all my appointments because I am not able to see them...)

---

### Post by NicoDietrich on 2010-01-14
I've had exactly the same problem and error messages as you, using korganizer-4.3-4 on Gentoo. Starting with "korganizer --nofork" resulted in a segmentation fault.

The following thread gave me the hint to take a look at my korganizerrc:
[http://lists.fedoraproject.org/pipermail/fedora-kde/2009-October/004365.html](http://lists.fedoraproject.org/pipermail/fedora-kde/2009-October/004365.html)

Renaming my ~/.kde4/share/config/korganizerrc to ~/.kde4/share/config/korganizerrc.weg indeed solved the problem and the program now starts again. (It might be that it's ~/.kde/share/config/korganizerrc in your Kubuntu)

Further analysis showed that only one line in the [Time & Date] section was the problem:
Holidays=de

Removing this line in my original file thus was sufficient. Afterwards German holidays don't show up anymore. When selecting a holiday region again in the Korganizer settings dialog, the program once more won't start.

I filed a bug report (with some more information): [https://bugs.kde.org/show_bug.cgi?id=222718](https://bugs.kde.org/show_bug.cgi?id=222718)

---

### Post by khelben1979 on 2010-01-14
What version of Ubuntu were you trying to upgrade to?

Also, have you considered the option of compiling it up from source?

---

