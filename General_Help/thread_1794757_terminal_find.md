---
title: "terminal find"
date: 2011-07-01
forum: General Help
---

### Post by flipper T on 2011-07-01
just reinstalled 10.04

loved 11.04 but kept breaking it

anyway, in 11.04 i could search terminal output using edit/find, if i remember correctly.

how do i do this in 10.04's terminal

tried ctrl f   :)

---

### Post by wolfen69 on 2011-07-01
```
locate filename
```

---

### Post by flipper T on 2011-07-01
sorry, i wasn't clear

what i need to do is search the output from the terminal for a specified string

eg: run a command & the terminal output is :

"hello welcome bon jour"

i want to search the output for all instances of "welcome" in the same manner you would search a web page with ctrl f

its do-able in 11.04

the only workaround i can think of is to copy and paste the output to a text editor and search from there, but the must be a more elegant solution.

---

### Post by nothingspecial on 2011-07-01
```
command | grep word
```

maybe

---

### Post by flipper T on 2011-07-01
that code doesn't _appear_ to do anything

---

### Post by nothingspecial on 2011-07-01
Not literally. Substitute "command" for your command, and "word" for your search term......


```
$ ls
Audiobooks       Dropbox            mpd       Radio      Tunes
Calibre Library  Ebooks             Music     source     Ubuntu One
Desktop          get_iplayer        Pictures  Templates  Videos
Documents        gpodder-downloads  Podcasts  test
Downloads        Images             Public    themes
$ ls | grep Documents
Documents
```

---

### Post by collisionystm on 2011-07-01
Or, if its a text file you want to search

cat /file | grep WORD

---

### Post by flipper T on 2011-07-01
thx for your time & reply but have found a solution

installed "Konsole" from the software center

i believe it's a kde console emulator & it does exactly what i need

thx again

---

### Post by nothingspecial on 2011-07-01
> **collisionystm said:**
> Or, if its a text file you want to search

cat /file | grep WORD
 
You don't need to pipe cat into grep, you can just grep the file -

```
grep word file
```

---

### Post by collisionystm on 2011-07-01
> **nothingspecial said:**
> You don't need to pipe cat into grep, you can just grep the file -

```
grep word file
```


Thanks! Didn't know that

---

### Post by nothingspecial on 2011-07-01
> **collisionystm said:**
> Thanks! Didn't know that

A common misconception. :p

```
cat file | less # wrong

less file # correct
```

There is no need to pipe a file from cat into another program that operates on files......

......although it works :D

---

### Post by sisco311 on 2011-07-01
> **nothingspecial said:**
> A common misconception. :p

```
cat file | less # wrong

less file # correct
```

There is no need to pipe a file from cat into another program that operates on files......

......although it works :D

It works, it works, but it drives me crazy when I see it. :)

It just makes the code slow. For example, yaourt is considerably slower than packer because it uses some  awkward code like *echo $(cat file| grep)*. See: [thread]1389872[/thread]

---

### Post by nothingspecial on 2011-07-01
> **sisco311 said:**
> It works, it works, but it drives me crazy when I see it. :)

It just makes the code slow. For example, yaourt is considerably slower than packer because it uses some  awkward code like *echo $(cat file| grep)*. See: [thread]1389872[/thread]

Don't let it upset you :D

If it works, it works <runs for cover>

---

### Post by AlphaLexman on 2011-07-01
> **collisionystm said:**
> cat /file | grep WORD
See: Useless Use of Cat, [http://partmaps.org/era/unix/award.html](http://partmaps.org/era/unix/award.html)

---

