---
title: "Help with wine on a virtual ISO"
date: 2010-10-26
forum: General Help
---

### Post by DirtyPC on 2010-10-26
Hello all, I do not currently have a DVD Drive, so I have Here Age Of Empires 3 on ISO, via Furius ISO mount. I know to use a .exe via wine, you have to right click it as executable, but when I do this I am told i do not have permission.
Any ideas? I'm stumped....
Thanks.

---

### Post by Verbeck on 2010-10-26
> **harrylucas1 said:**
> Hello all, I do not currently have a DVD Drive, so I have Here Age Of Empires 3 on ISO, via Furius ISO mount. I know to use a .exe via wine, you have to right click it as executable, but when I do this I am told i do not have permission.
Any ideas? I'm stumped....
Thanks.
try using the terminal
first to go to the mounted iso directory:

```

cd /media/iso/

```just replace the **/media/iso/** with where the iso is actually mounted. if the dirrectory contains 'spaces' then use a **\** before each space

then run 
```
wine actualname.exe
```

---

### Post by DirtyPC on 2010-10-26
> **Verbeck said:**
> try using the terminal
first to go to the mounted iso directory:

```

cd /media/iso/

```just replace the **/media/iso/** with where the iso is actually mounted. if the dirrectory contains 'spaces' then use a **\** before each space

then run 
```
wine actualname.exe
```

Hello done that, now when it asks me to enter a product key during set up (which is genuine) it says something about a dll error not in the right place?

---

### Post by Verbeck on 2010-10-26
try the wine appdb.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795)

---

### Post by DirtyPC on 2010-10-26
> **Verbeck said:**
> try the wine appdb.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795)
Winehq doesnt know anything about the virtualISO stuff

---

### Post by Verbeck on 2010-10-26
> **harrylucas1 said:**
> Winehq doesnt know anything about the virtualISO stuff
i dont think it matters if its a cd or an iso if you can access it :|

also, scroll down a bit and you'll see detailed HOWTO's

---

### Post by DirtyPC on 2010-10-27
Right... I managed to get it working... :KS,
:confused:BUT:confused:


When it loads, sometimes theres sound, sometimes theres not, and i changed the window size to 800x600 and now whenever I click on it I get, monitor out of range?

GRrrrrrr

---

### Post by Verbeck on 2010-10-27
the sound issue was pointed out in wineabbdb
as for the resolution problem, i'v got no experience with that particular error within wine, but *maybe* setting the refresh rate and/or resolution from within the game to a lower value might fix it

---

### Post by DirtyPC on 2010-10-31
> **Verbeck said:**
> the sound issue was pointed out in wineabbdb
as for the resolution problem, i'v got no experience with that particular error within wine, but *maybe* setting the refresh rate and/or resolution from within the game to a lower value might fix it
I got it fixed, but it's to buggy for my liking, its off my HDD now.

---

