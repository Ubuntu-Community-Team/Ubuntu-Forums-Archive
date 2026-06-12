---
title: "Directory exists but bash says it doesn't"
date: 2011-08-19
forum: General Help
---

### Post by cbrick77 on 2011-08-19
So I've run into a problem with my bash program.

```
a
mkdir -p /home/chris/Downloads/ARCHIVE/`date -I`
find /home/chris/Downloads* -mtime +14 -exec "cp {} /home/chris/Downloads/ARCHIVE/`date -I` \ ;

```

It's meant to move old files from my Downloads folder into an archive file (later tar them). The directory exists, I've used $PWD and nautilus and ls to make sure it's there, yet for every file it gives 

```
find: `cp /home/chris/Download/foo.bar /home/chris/Downloads/ARCHIVE/2011-08-19': No such file or directory
```

I tried to test it on a different destination, specifically my home folder. IT still gave me the error.

IS it a bad syntax within find or something else? I'm running a 32-bit system with 11.04

---

### Post by deserthowler on 2011-08-19
> **cbrick77 said:**
> So I've run into a problem with my bash program.

```
a
mkdir -p /home/chris/Downloads/ARCHIVE/`date -I`
find /home/chris/Downloads* -mtime +14 -exec "cp {} /home/chris/Downloads/ARCHIVE/`date -I` \ ;

```



Should that be ```
find /home/chris/Downloads[COLOR="Red"]/[/COLOR]* -mtime +14 -exec "cp {} /home/chris/Downloads/ARCHIVE/`date -I` \ ;
```

Earl

---

### Post by cbrick77 on 2011-08-20
Gave the same output as it did without the extra / but it's probably better to put it in anyway...

Still says they don't exist...

---

### Post by WyleECoyote on 2011-08-20
you just forgot to add a few things, this is what it should look like:

```
find /home/chris/Downloads -mtime +14 [color=#FF0000]-type f[/color] -exec cp [color=#FF0000]'[/color]{}[color=#FF0000]'[/color] /home/chris/Downloads/ARCHIVE/`date -I` \;
```

---

### Post by cbrick77 on 2011-08-20
Worked like a charm, thanks.

---

