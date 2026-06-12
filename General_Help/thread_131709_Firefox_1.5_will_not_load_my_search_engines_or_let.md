---
title: "Firefox 1.5 will not load my search engines or let me save bookmarks"
date: 2006-02-16
forum: General Help
---

### Post by matthew on 2006-02-16
My turn to ask a question...

I upgraded to Firefox 1.5.0.1 using the instructions on this wiki page: [https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")

Everything worked beautifully, just as listed.

After the thrid of fourth time I opened Firefox I noticed it had returned to it's usual "first time using the program" size (window height x width) and thought that was odd as it usually would open however I had resized it when I closed it the previous time.

Then I noticed I have no search engines available in the upper right hand corner drop down menu where I usually have 10 or so.

Then I tried to make a new bookmark and discovered that I couldn't...Firefox just won't let me.

I found the location in /home where the new Firefox settings and stuff are kept and there is a sub directory called search that has all my search engines in it. My bookmarks file is in there as well.

Does anyone have any idea as to what may be going on here? I've looked at file permissions and searched high and low and can't come up with anything.

Worst case scenario I'll just delete FF 1.5 and reinstall, but this is weird and I'm innately curious.

---

### Post by towsonu2003 on 2006-02-17
did you check the permissions? ```
ls -l ~/.mozilla/firefox
```

---

### Post by matthew on 2006-02-17
It's acting like a permissions problem, but I can't seem to find a specific file with a problem.

Does this look right to you? I can't see anything that would seem problematic...but then what do I know?
```
ls -l ~/.mozilla/firefox
total 20
drwxr-xr-x  7 matt matt 4096 2006-02-17 10:26 f1c4wrc2.default
drwxr-xr-x  4 matt matt 4096 2006-02-10 16:29 ff1.5
-rw-r--r--  1 matt matt 7809 2006-02-15 16:39 pluginreg.dat
-rw-r--r--  1 matt matt   94 2006-02-10 16:26 profiles.ini

```

---

### Post by jrib on 2006-02-17
If the old version of firefox is opened, it messes up your settings.  Did that ever happen?

---

### Post by aysiu on 2006-02-17
Have you tried this? ```
firefox -safe-mode
``` If it launches, export your bookmarks and then ```
mv ~/.mozilla ~/.mozilla_backup
firefox
``` then reimport the bookmarks?

---

### Post by matthew on 2006-02-17
[quote=aysiu]Have you tried this? ```
firefox -safe-mode
``` If it launches, export your bookmarks and then ```
mv ~/.mozilla ~/.mozilla_backup
firefox
``` then reimport the bookmarks?[/quote]That worked beautifully. Thanks, aysiu!!

---

