---
title: "Two files with the same name in same directory"
date: 2011-12-23
forum: General Help
---

### Post by djeyewater on 2011-12-23
I seem to have two files with the same name (Places.kml) in a directory:

```
ls -lbF
total 3964
-rw-r--r-- 1 djeyewater djeyewater   33783 2011-12-21 16:11 Abstract.kml
-rw-r--r-- 1 djeyewater djeyewater     897 2010-09-13 19:36 Dynamic.kml
-rw-r--r-- 1 djeyewater djeyewater   57226 2011-12-21 16:11 Events.kml
-rw-r--r-- 1 djeyewater djeyewater  991037 2011-12-21 16:11 Life.kml
-rw-r--r-- 1 djeyewater djeyewater    9682 2011-12-21 16:11 Miscellaneous.kml
-rw-r--r-- 1 djeyewater djeyewater   25251 2011-08-11 19:26 &#65279;Places.kml
-rw-r--r-- 1 djeyewater djeyewater 2915081 2011-12-21 16:11 Places.kml
```

Any idea how this can happen?

---

### Post by Lars Noodén on 2011-12-23
Is there whitespace in the name of one of them at the end of the name?

```

for i in *;do echo '"'${i}'"';done

```

---

### Post by djeyewater on 2011-12-23
No, that shows:
```
for i in *;do echo '"'${i}'"';done
"Abstract.kml"
"Dynamic.kml"
"Events.kml"
"Life.kml"
"Miscellaneous.kml"
"&#65279;Places.kml"
"Places.kml"
```

---

### Post by HermanAB on 2011-12-23
Hmm, the files are managed by inode number, but the names should always be unique.  Try renaming one of them using a GUI file manager such as Nautilus, so that you can mouse select it without having to type the name.

---

### Post by djeyewater on 2011-12-23
Thanks, i have deleted it in Nautilus as you suggested now. I didn't realise Linux allowed having identically named files in the same location.

---

### Post by The Cog on 2011-12-23
It doesn't. either there was a bad screw-up in the file system, or more likely to my mind, there was an unprintable character in one of the file names.

---

