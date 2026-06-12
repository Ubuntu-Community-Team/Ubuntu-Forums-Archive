---
title: "Rename music files with CLI"
date: 2011-07-11
forum: General Help
---

### Post by Random_Dude on 2011-07-11
Hi everyone.

I'm trying to organise some music files, but doing it by hand is boring and not very efficient. So I was wondering if anyone would help me do it trough command line.

The music files as named like the following: 01 Music Title. I would like to get them as: Band Name - Music Title.
I looked into the rename command and I was thinking of doing something like this:
```
rename "s/(the first two integers)/Band Name -/g" *.mp3
```The problem is that I don't know how to indicate the first two integers. Does anyone know how to do this?

---

### Post by dethorpe on 2011-07-11
Not used rename, but if its a standard reguler expression something like this:
 
s/^[0-9]{2}/Band Name -/
 
Shouldn't need the 'g' modifier as you only want to change the 1st match.
 
best try in a test directory with a few files 1st, to make sure it does what you want :-)

---

### Post by Random_Dude on 2011-07-11
> **dethorpe said:**
> Not used rename, but if its a standard reguler expression something like this:
 
s/^[0-9]{2}/Band Name -/
 
Shouldn't need the 'g' modifier as you only want to change the 1st match.
 
best try in a test directory with a few files 1st, to make sure it does what you want :-)

That's exactly it, thanks! ;)

BTW, you can test it before you rename by typing:
```
rename -n "s/^[0-9]{2}/Band Name -/" *.mp3
```Cheers :cool:

---

