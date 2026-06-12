---
title: "Find and replace with sed at beginning of a word"
date: 2010-11-15
forum: General Help
---

### Post by geo909 on 2010-11-15
Hello all,

I want to write a small script to rename a bunch of files. Their name is of the form 'long number'|'name'|'extension', for example:

52354Football_part2.flv
2353452Nice_weather_4_ducks.flv

I would like to rename these to:

Football_part2.flv
Nice_weather_4_ducks.flv

If in my script I use something like 
```
sed s/[0-9]//g 
```
on each file, I will get
*Football_part.flv*, instead of *Football_part2.flv*,
and
*Nice_weather__ducks.flv*, instead of *Nice_weather_4_ducks.flv*.

Could you tell me how to instruct sed to only remove numbers that are *in the beginning* of the name
in a simple way?

Thank you very much in advance

---

### Post by DaithiF on 2010-11-15
```
sed 's/^[0-9]\+//'
```where ^ anchors the pattern to the beginning of the line

Edit: you might also want to look into the rename command, which takes a perl regexp and applies it to filenames -- it offers some useful features like a dummy mode to show what changes it would apply (without actually applying them).

---

### Post by geo909 on 2010-11-15
Thanks so much, that makes sense! Ah, I'm not so familiar yet with reg. expressions..

---

