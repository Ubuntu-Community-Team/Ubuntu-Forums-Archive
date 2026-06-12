---
title: "MOC doesn't display my music ( .mp3 ) - how to fix it ?"
date: 2009-09-16
forum: General Help
---

### Post by sunchiqua on 2009-09-16
```
moc 2.4.4 Build: Sep 17 2009 00:32:26
Compiled with: OSS ALSA DEBUG

```

Is there a way to fix it ?

---

### Post by por100pre1 on 2009-09-16
This is the version that I have, it is version from the repos:

```
moc 2.5.0-alpha3 Build: Nov 17 2008 21:26:11
Compiled with: OSS ALSA JACK DEBUG internet streams resample

```

Weird. Are you sure you are using the version from the repos?

Have you checked the permissions of your music folder? Check the id tags of the files too.

---

### Post by sunchiqua on 2009-09-16
> **por100pre1 said:**
> This is the version that I have, it is version from the repos:

```
moc 2.5.0-alpha3 Build: Nov 17 2008 21:26:11
Compiled with: OSS ALSA JACK DEBUG internet streams resample

```Weird. Are you sure you are using the version from the repos?

Have you checked the permissions of your music folder? Check the id tags of the files too.


[LIST=1]
[*]I compiled it on my own - it's not from repositories
[*]Permissions are as they should be
[/LIST]
I thought I should try repos version, but .. I've another problem - there's something missing ( see attached file ).

---

### Post by por100pre1 on 2009-09-16
Please try the version from the repositories. It seems the compiled version doesn't have mp3 support.

---

### Post by sunchiqua on 2009-09-16
> **por100pre1 said:**
> Please try the version from the repositories. It seems the compiled version doesn't have mp3 support.

I already did it ( see my previous post ) .. something is still missing.

**UPDATE ::** tried it on LiveCD and it works. Weird! Looks like compiled version screwed something up and I can't seem to find a way to fix it.

---

### Post by por100pre1 on 2009-09-16
> **sunchiqua said:**
> [LIST=1]
[*]I compiled it on my own - it's not from repositories
[*]Permissions are as they should be
[/LIST]
I thought I should try repos version, but .. I've another problem - there's something missing ( see attached file ).

Sorry, try making copies of the affected files and convert those copies with Sound Converter...

UPDATE:Try uninstalling and removing every trace of mocp and reinstalling.

---

### Post by sunchiqua on 2009-09-16
> **por100pre1 said:**
> 
UPDATE:Try uninstalling and removing every trace of mocp and reinstalling.

Done ( x10 ) - still no luck :(

---

### Post by por100pre1 on 2009-09-16
> **sunchiqua said:**
> Done ( x10 ) - still no luck :(

Are all mp3 files affected by that issue?

---

### Post by sunchiqua on 2009-09-16
> **por100pre1 said:**
> Are all mp3 files affected by that issue?

Yes. Anyway, I've successfully reinstalled Ubuntu @ installed MOC from repositories - works just fine :) As this is my "experimental" machine .. fy.

---

