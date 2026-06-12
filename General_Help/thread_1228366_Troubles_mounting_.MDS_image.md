---
title: "Troubles mounting .MDS image"
date: 2009-07-31
forum: General Help
---

### Post by nokvok on 2009-07-31
Hello,  I have troubles mounting a .MDS file. I've tried Gmount-iso, gISOmount and MountManager. Gmount gives an error message for unsupported format, gISO freezes and Mount Manager does nothing. There is no evidence that the file is damaged either.  I am relatively new to Ubuntu, so there is a chance I missed something simple, but I've tried a lot already.  If anyone got advice, I'd appreciate it.  Thanks.

---

### Post by Kai Summers on 2009-07-31
[COLOR=#008000][COLOR=Black]In terminal type:

[COLOR=DarkGreen]sudo mount -o loop /path/to/file.mds  /movies/[/COLOR]

This should mount your .mds file.[/COLOR]  
[/COLOR]

---

### Post by yabbadabbadont on 2009-07-31
Have you seen this?  [http://ubuntuforums.org/showthread.php?t=1203871](http://ubuntuforums.org/showthread.php?t=1203871)

---

### Post by nokvok on 2009-07-31
The mount line requests me to put a file systemtype as parameter, but the Manual tells me mds is not supported.   I have indeed not thought about simply converting the image to iso. And while the cat command created an iso, this iso triggers the same error message with gmount as the mds.  I will continue to try the program recommended in that linked thread, though I am still not used to manually install software.  Thanks for now.

---

### Post by yabbadabbadont on 2009-07-31
Wikipedia states that CDemu can also mount MDS files.

[http://en.wikipedia.org/wiki/CDemu](http://en.wikipedia.org/wiki/CDemu)

---

### Post by Bonster on 2009-08-01
Get this [http://www.getdeb.net/app/AcetoneISO](http://www.getdeb.net/app/AcetoneISO)

---

