---
title: "uninstallation question!!"
date: 2009-09-17
forum: General Help
---

### Post by bobigeorge on 2009-09-17
Hello friends,

Today I installed and tried an application called "rarcrack" 
And found of no use. Now I wanted to uninstall it. 

I have tried ```
sudo apt-get remove rarcrack
``` and ```
sudo apt-get --purge remove rarcrack
```

The output was ```
Package rarcrack is not installed, so not removed
```

But the application is still there and is working

Throw me some light :-)

---

### Post by dabang on 2009-09-17
I don't know this app, but I'd guess you installed from source? At least it's not in the default Ubuntu repositories (and the name seems a little suspicious to me..). If not installed via package manager, it's not uninstallable by the package manager... Remove the files manually or hope the make command has an uninstall target. (Just the way you installed it, but this time 'make uninstall').

---

### Post by bobigeorge on 2009-09-17
Thanks dabang for the quick reply

Nothing suspecious.. The application promised to break password protected rar/zip files. So I just wanted to try it on protected archieves *created by me*.

But it proved to be successful in only two character passwords. 

And I installed it from a .deb package...!!!!

---

### Post by marcopolo1981 on 2009-09-17
Try synaptic package manager>local and obsolete.
If it is listed there, it should allow you to remove it.

---

### Post by bobigeorge on 2009-09-17
Yea I tried synaptic too. 
The strange thing is that the package is not listed there.

---

### Post by wojox on 2009-09-17
```
locate rarcrack
```

Then delete all instances.

---

### Post by bobigeorge on 2009-09-17
Is it a good uninstall by locating and deleting all instances?? Share some knowledge...

---

### Post by wojox on 2009-09-17
Try:

```
sudo dpkg -r rarcrack
```

---

### Post by bobigeorge on 2009-09-18
```
list rarcrack
``` has generated the following

```
/rarcrack
/usr/bin/rarcrack
/usr/share/doc/rarcrack
/usr/share/doc/rarcrack/CHANGELOG
/usr/share/doc/rarcrack/LICENSE
/usr/share/doc/rarcrack/README
/usr/share/doc/rarcrack/README.html
/usr/share/doc/rarcrack/RELEASE_NOTES
/var/lib/dpkg/info/rarcrack-compdigitec-unofficial.list

```

but 

> sudo dpkg -r rarcrack resulted

```
dpkg - warning: ignoring request to remove rarcrack which isn't installed.
```

??!!

---

