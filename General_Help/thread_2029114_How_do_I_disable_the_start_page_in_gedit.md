---
title: "How do I disable the start page in gedit?"
date: 2012-07-19
forum: General Help
---

### Post by sienile on 2012-07-19
Title pretty much says it all. I want to disable the start page that opens up every time you open gedit.

To me the page is a bit of a nuisance. Gedit always opens the page, even when I'm opening a file. I'm pretty sure it's part of the reason why gedit takes an extra 5 seconds to boot up. 5 seconds may not seem like much, but it's enough time for me to forget what I was going to type. :P

---

### Post by papibe on 2012-07-19
Hi sienile.

I've never seen that behaviour on gedit, so I assumed it is a plugin.

This one maybe:  reopen-tabs-gedit-plugin (Loads recently opened documents when gedit starts)

Go to:
```
Edit -> Preferences -> Plugins
```
and disable it there. Then restart Gedit.

Let us know how it goes.
Regards.

---

### Post by sienile on 2012-08-11
After a fresh re-install of Ubuntu I still have a similar problem. (The start page was a plugin that I installed, but did not show up in the Plugin Preferences tab somehow.)

Now whenever I open a file by clicking it in a file manager (but not when using gedit's open dialog) it **opens an extra blank document.** It doesn't cause gedit to be slow opening like the start page did, but it's still annoying to have to close all the extra blank docs when I open a series of files.

P.S.: Gedit has absolutely no additional plugins installed. It's the out-of-the-box Ubuntu 12.04 X86_64 installation.

---

### Post by ads52 on 2012-08-12
Indeed that is a little odd, I also have a new installation of 12.04 and gedit does not show this behaviour, simply opens quickly with a single '*Untitled Document 1*' in place when opened via Dash and when accessing files from a File Manager 2ble click it opens only the requested file. Perhaps disable all Gedit plugins and try again? Then slowly reintroduce the plugins one by one.

Mind you have a look at this thread, particularly posts 6 and 7 which seem to point to a solution:

[https://bbs.archlinux.org/viewtopic.php?id=120283](https://bbs.archlinux.org/viewtopic.php?id=120283)

Looks like you are not alone :).

---

### Post by sienile on 2012-08-12
Thanks, ads52. I had looked everywhere for someone having a similar issue. Guess I just wasn't using the right keywords to find it.

---

### Post by sienile on 2012-08-12
While the steps in the forum posts ads52 pointed me to did not work, they put me in the right direction.

To fix the blank page problem, you must edit /usr/share/applications/gedit.desktop

The line that says: ```
Exec=gedit %U
```

Change to
```
[S]Exec=gedit $1[/S]
```

That was what worked for me, but others have reported success and failure with each of the following:
```

Exec=gedit $1 < /dev/null
Exec=gedit "$1" < /dev/null
Exec=gedit %u

```
Note that the last one is a lowercase U instead of the default capital.

I believe the ones containing /dev/null are KDE solutions, mine and the %u are Gnome solutions.

---

### Post by sienile on 2012-08-12
Okay... this is ticking me off. After I reported this as solved, the very next file I opened in gedit caused the blank page to pop back up. ](*,) :-x

I'm going to tinker with it some more and see what happens.

---

### Post by ads52 on 2012-08-12
Thanks for both researching the problem and posting the final solution :).

---

### Post by sienile on 2012-08-12
Apparently I was being a bit too hasty with with trying each solution. It seems to take Ubuntu a few seconds more than I thought to update the application database automatically. 

After retrying each solution and waiting a full minute after each, the solution that *actually* worked for me was:
```
Exec=gedit $1 < /dev/null
```

Post finally solved. :P

---

