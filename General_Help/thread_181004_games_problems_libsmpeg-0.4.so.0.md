---
title: "games problems: libsmpeg-0.4.so.0"
date: 2006-05-23
forum: General Help
---

### Post by DarkFox-DK on 2006-05-23
When i try to start some games/apps (like tdfsb, bomberclone and frozen-bubble) i get this error
```
./tdfsb: error while loading shared libraries: libsmpeg-0.4.so.0: cannot open shared object file: No such file or directory
```
What to do??? i tried apt-getting libsmpeg-dev, but that didnt help...

---

### Post by gerbman on 2006-05-23
[QUOTE=DarkFox-DK]When i try to start some games/apps (like tdfsb, bomberclone and frozen-bubble) i get this error
```
./tdfsb: error while loading shared libraries: libsmpeg-0.4.so.0: cannot open shared object file: No such file or directory
```
What to do??? i tried apt-getting libsmpeg-dev, but that didnt help...[/QUOTE]Open a terminal and type```
ls -l /usr/lib | grep libsmpeg
```What is the output?

---

### Post by DarkFox-DK on 2006-05-25
```
-rw-r--r--   1 root root   307440 2005-11-16 11:56 libsmpeg.a
-rw-r--r--   1 root root      730 2005-11-16 11:56 libsmpeg.la
lrwxrwxrwx   1 root root       21 2006-05-22 02:12 libsmpeg.so -> libsmpeg-0.4.s o.0.1.4
```

---

### Post by gerbman on 2006-05-25
[QUOTE=DarkFox-DK]```
-rw-r--r--   1 root root   307440 2005-11-16 11:56 libsmpeg.a
-rw-r--r--   1 root root      730 2005-11-16 11:56 libsmpeg.la
lrwxrwxrwx   1 root root       21 2006-05-22 02:12 libsmpeg.so -> libsmpeg-0.4.s o.0.1.4
```[/QUOTE]That's strange. libsmpeg.so links to libsmpeg-0.4.so.0.1.4, which isn't present. Did you create that link? Here's the output of the command on my machine:```
lrwxrwxrwx   1 root root       21 2006-04-09 02:31 libsmpeg-0.4.so.0 -> libsmpeg -0.4.so.0.1.4
-rw-r--r--   1 root root   242408 2005-08-03 11:50 libsmpeg-0.4.so.0.1.4
```it should look something like that. Did you install the libsmpeg0c2 package (that is a zero and a two in the package name)? If not, do so and post the output of "ls -l /usr/lib | grep libsmpeg" again.

---

### Post by DarkFox-DK on 2006-05-25
[quote=gerbman]Did you install the libsmpeg0c2 package (that is a zero and a two in the package name)? If not, do so and post the output of "ls -l /usr/lib | grep libsmpeg" again.[/quote] 
yes i have libsmpeg0c2, i just recompiled my kernel and reinstalled the nvidia driver because the X server and nvidia driver f***** up somehow, and now i can't play any games at all...

```
root@darkfox-server:/usr/games# ./bzflag
Segmentation fault
root@darkfox-server:/usr/games# ./armagetron
Segmentation fault
root@darkfox-server:/usr/games# ./ppracer
./ppracer: error while loading shared libraries: libsmpeg-0.4.so.0: cannot open shared object file: No such file or directory

``` 
i have tried removing and reinstalling the games, but with no results at all :(

maybe a little off topic but im considering installing Kubuntu instead because i like KDE better, is that a really really bad idea?

---

### Post by gerbman on 2006-05-25
[QUOTE=DarkFox-DK]i have tried removing and reinstalling the games, but with no results at all :([/QUOTE]The problem isn't the games, it's the fact that they can't find libsmpeg-0.4.so.0. You could try installing the libsmpeg package from the Debian [site]("http://packages.debian.org/stable/libs/libsmpeg0")...it lists libsmpeg-0.4.so.0 as a contained file.

> maybe a little off topic but im considering installing Kubuntu instead because i like KDE better, is that a really really bad idea?
I don't see any reason why this is a bad idea. You don't have to do a clean install though, just install the "kde" package. I've tried KDE on a couple occasions, but always seem to come back to GNOME :-)

Good luck.

---

### Post by DarkFox-DK on 2006-05-25
[quote=gerbman]You could try installing the libsmpeg package from the Debian [site]("http://packages.debian.org/stable/libs/libsmpeg0")...it lists libsmpeg-0.4.so.0 as a contained file.[/quote] Installed the package from the debian site, it had no effect at all..

Ive allready pulled out my extra harddisk and is about to start making backups, format and install Kubuntu

seems like im better at f*ck*ng linux up than window$ :-P ;)

---

