---
title: "Listen to NPR (National Public Radion)"
date: 2010-04-14
forum: General Help
---

### Post by fantastic on 2010-04-14
Is there a way to listen to listen to NPR on linux, and not through a browser? 

I tried this [post]("http://ubuntuforums.org/showthread.php?t=432369"), but I could not get it working. What URL should I add as a radio station in Rhythbox, or a different player.

---

### Post by Mighty_Joe on 2010-04-14
my local NPR station has an [MP3 stream]("http://wksu.org/listen/wksu1.pls").  I saved it to disk and opened it with Audacious.

---

### Post by ron999 on 2010-04-14
There's also a '24 hour stream'.
The url can be used with mplayer or vlc or rhythmbox etc.
```
http://npr.ic.llnwd.net/stream/npr_live24
```

---

### Post by fantastic on 2010-04-14
> **ron999 said:**
> There's also a '24 hour stream'.
The url can be used with mplayer or vlc or rhythmbox etc.
```
http://npr.ic.llnwd.net/stream/npr_live24
```


Super fantastic! Thanks! This is exactly what I was looking for.

---

### Post by fantastic on 2010-09-20
My apologies... 

Edit rhythmdb.xml. (*My particular rhythmdb.xml was located in /home/{USER}/.local/share/rhythmbox/rhythmdb.xml*)

Here is the configuration:


```
  <entry type="iradio">
    <title>NPR</title>
    <genre>News</genre>
    <artist></artist>
    <album></album>
    <location>http://npr.ic.llnwd.net/stream/npr_live24</location>
    <date>0</date>
    <mimetype>application/octet-stream</mimetype>
    <mb-trackid></mb-trackid>
  </entry>

```

Hope that helps you.

---

### Post by Rent_A_Pig on 2010-09-20
> **fantastic said:**
> Is there a way to listen to listen to NPR on linux, and not through a browser? 
 
I tried this [post]("http://ubuntuforums.org/showthread.php?t=432369"), but I could not get it working. What URL should I add as a radio station in Rhythbox, or a different player.
 
 
DOCKY has a app for that. :P

---

