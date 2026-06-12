---
title: "Firefox randomly crashing"
date: 2012-08-28
forum: General Help
---

### Post by chellrose on 2012-08-28
I just installed Ubuntu 11.10 about a week ago.  Now Firefox randomly crashes at various times.  I have Firefox 14.0.1, no add-ons except for what comes with the default package.

Firefox almost always crashes whenever I download a file.  It can also crash at other random times when I'm browsing the web.  I never see any kind of crash dialog.  If I run it from the terminal, I see the message
```
 (firefox:10547): Gtk-CRITICAL **: IA__gtk_entry_get_text: assertion `GTK_IS_ENTRY (entry)' failed
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = gtk-qt-application path = <unknown> pid = 10547

[1]+  Segmentation fault      firefox

```

I've run into at least one other (presumably) unrelated issue with gtk version conflicts (see [this thread]("http://ubuntuforums.org/showthread.php?p=12203153")).  Ubuntu (or maybe TDE) seems to have 2 versions of gtk installed.  Trouble is, I don't know how to determine which one to uninstall without breaking things...

Any thoughts?

---

### Post by chellrose on 2012-08-29
So apparently the error messages in terminal are slightly different depending on the crash.  The one in my previous post occurred when Firefox just randomly crashed while I was browsing the web.  Today I saved a file to my HD, and got this error message:

```

(firefox:309): Gtk-CRITICAL **: IA__gtk_entry_get_text: assertion `GTK_IS_ENTRY (entry)' failed
KCrash: crashing... crashRecursionCounter = 2
[warn] epoll_wait: Bad file descriptor
[warn] epoll_wait: Bad file descriptor
[warn] epoll_wait: Bad file descriptor

#### That line is repeated a bunch of times (estimate ~50), then

KCrash: Application Name = gtk-qt-application path = <unknown> pid = 309

[1]+  Segmentation fault      firefox

```Almost exactly like the last one, but not quite.  The only difference I observe is the 50 or so lines of "[warn] epoll_wait: Bad file descriptor".  But hopefully that is helpful.

Firefox was updated today, and the problem still exists.

---

### Post by chellrose on 2012-09-29
](*,)
Was hopeful that the last few rounds of Firefox updates would have fixed this, but no such luck.

---

### Post by chellrose on 2013-02-01
Not trying to unnecessarily bump an old thread, but I didn't find this issue anywhere else on UF.  In case anyone else should ever have the aforementioned Firefox-crashing problem in TDE: Here's the solution, straight from their website:

> kgtk-qt3-trinity can cause certain applications to crash.  If you  experience crashes try removing this package, but note that you will  lose TDE open/save dialogs in all applications.

Of course, removing this package results in several other weird quirks in various programs, but I haven't found any yet that have a significant negative impact on my computing experience. :)

---

