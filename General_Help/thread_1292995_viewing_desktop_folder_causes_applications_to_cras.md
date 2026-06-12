---
title: "viewing desktop folder causes applications to crash"
date: 2009-10-16
forum: General Help
---

### Post by twdsje on 2009-10-16
I have an issue where browsing to the desktop folder in certain applications will cause that particular application to crash.  For instance if I go into firefox 3.5 and select "save page as" the application will immediately close.  The same issue occurs in Aptana.  If I go to open a file everything is fine until I click on the desktop folder.  The error is consistent, and happens only when the save/open dialog tries to view the Desktop folder.  However, it doesn't happen in all applications.  For instance dolphin and kscreenshot seem to be just fine.  

when I do the dmesg command I get lines like these:

```
[  275.398596] firefox-bin[3786]: segfault at 6972656e ip 6972656e sp a60fe07c error 4
[  341.829030] firefox-bin[3816]: segfault at a94541b4 ip aa48ca6e sp bf8f8ce4 error 4 in libflashplayer.so[aa452000+990000]
[  360.167131] crashreporter[3853]: segfault at b6ed9d50 ip b6ed9d50 sp bfd1caec error 4 in libqtcurve.so[b6f23000+2e000]
[  485.421015] crashreporter[4291]: segfault at b6ef8d50 ip b6ef8d50 sp bfd39b0c error 4 in libqtcurve.so[b6f42000+2e000]
```

Here are the contents of the folder:

```
ls -la
total 2408
drwxr-xr-x  2 twdsje twdsje    4096 2009-10-14 16:17 .
drwxr-xr-x 64 twdsje twdsje    4096 2009-10-16 12:04 ..
lrwxrwxrwx  1 twdsje twdsje      43 2009-09-16 11:01 AptanaStudio -> /home/twdsje/Aptana Studio 1.5/AptanaStudio
-rw-r--r--  1 twdsje twdsje    1989 2009-09-16 15:09 .directory
lrwxrwxrwx  1 twdsje twdsje      28 2009-09-15 10:04 firefox -> /home/twdsje/firefox/firefox
-rw-r--r--  1 twdsje twdsje 2438553 2009-09-14 11:44 hlrb.pdf
-rwx------  1 twdsje twdsje     360 2009-09-14 15:14 klok.af6b2973d903bfae0589c27890fe0146c233490a.1.desktop
lrwxrwxrwx  1 twdsje twdsje      44 2009-09-17 08:32 konsole.desktop -> /usr/share/applications/kde4/konsole.desktop
-rwx------  1 twdsje twdsje     502 2009-10-12 14:50 stocktwits.8986d6b7d178aac41a95020d78f34b5073f31dbb.1.desktop
```

I am using latest Kubuntu desktop beta.  Everything is updated.

---

### Post by sundoulos on 2009-11-25
same issue here in kubuntu 9.04. Have you found a fix yet? It's really annoying not to be able to use the file browser in firefox, gimp, acrobat reader, etc.

---

### Post by twdsje on 2009-11-25
When I updated to the new version (9.10) the problem went away along with a few other oddities (IE I couldn't resize windows).

---

### Post by sundoulos on 2009-11-26
Wonderful (slight sarcasm)! Hopefully the next attempt at upgrading to 9.10 is more successful. Took 2 days to recover the last time; ended up going back to 8.04, then 8.10, then 9.04 to get something working again. Oh well!

---

### Post by Zorael on 2009-11-27
I had an issue once where Dolphin crashed when I viewed a particular directory. When I launched dolphin from a terminal it was able to spout some error output before it died, suggesting one of the files had such an unsane creation date that the app couldn't cope. I never really found a fix for this, as my terminal-fu is not strong enough to change dates of files.

This was in 4.1 or so, long since I ran into it.

---

