---
title: "Remote keyboard over SSH?"
date: 2009-09-08
forum: General Help
---

### Post by dabbi2000 on 2009-09-08
Hi,
I want to control another linux computer's media player by keyboard only (eg pressing media key right switches song). It's in the same house (=> LAN connected) and so I wonder if I can grab control over the other computer's keyboard through SSH? I don't want to do the whole remote desktop, just minimal bandwith and max speed!

---

### Post by GoldenSun on 2009-09-08
I am kind of confused here on what you want.  
You can control a media player through ssh and have it play on the computer that you ssh'd into.
I think it's something like this
```

mplayer /path/to/song.mp3

```

I haven't had any success with other media players besides mplayer.

---

### Post by baseface on 2009-09-08
vnc?

---

### Post by baseface on 2009-09-08
read this [http://ubuntuforums.org/archive/index.php/t-571391.html](http://ubuntuforums.org/archive/index.php/t-571391.html)

---

