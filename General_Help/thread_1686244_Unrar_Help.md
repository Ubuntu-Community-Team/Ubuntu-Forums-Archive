---
title: "Unrar Help"
date: 2011-02-12
forum: General Help
---

### Post by Teh_Messiah on 2011-02-12
Hi all,
I have searched the forums already for my problem and the only answer i got didn't work.
I have downloaded a tv series which are rared into *.rar01 format.
There are no plain .rar files in it and using this code i found earlier doesn't work.
```
find -type f -name '*.rar' -exec unrar x {} \;
```
I tried altering it to this to rectify the problem however it didn't.
```
find -type f -name '*.rar01' -exec unrar x {} \;
```
If I type
```
find *.rar01
```
with or without being wrapped in '' I get no results.
I'm in the
/series/
directory of 
/series/episode-1(2,3,4,5,6...)/files.rar01(.rar02,03,04,05,06....)
There are 8 seasons with over 20 episodes in each season and it is very annoying typing this 20+ times for each season.
```
sudo unrar e episode-directory/files.rar01 /target/directory/
```
Please help!

---

### Post by williamts99 on 2011-02-12
> **Teh_Messiah said:**
> I have downloaded a tv series which are rared into *.rar01 format.
There are no plain .rar files in it and using this code i found earlier doesn't work.

When they are in parts like that, just right click on the first one in nautilus and choose 'extract here'.

If they are in rar3 format, you will have to use WINE to run WinRAR to extract. [http://www.rarlab.com/rar_add.htm](http://www.rarlab.com/rar_add.htm)

---

### Post by Teh_Messiah on 2011-02-12
Yeah but I am unpacking them on my server and want to unrar the whole season at once instead of doing it individually.
For example 8 seasons x 20 episodes each (at least) 160 episodes to unrar!

---

### Post by Jose Catre-Vandis on 2011-02-12
How about this?

```
find . -type f -name '*.rar01' -exec unrar x "{}" \;
```

This and your command works fine on rar files named .rar01 for me. (You need to be in the right directory!)

Also could trymodifying this command I have as a thunar custom action:

```
xfce4-terminal -x /usr/bin/unrar e -y %f
```

So just running:

```
/usr/bin/unrar e -y "*.rar01"
```
should do it

---

### Post by Teh_Messiah on 2011-02-13
```
unrar x
```
didn't work for me, however ```
unrar e
``` did for *.rar files.
I'm about to try your code and see what happens :)
I'll keep you posted

---

### Post by Teh_Messiah on 2011-02-13
```
find . -type f -name '*.rar01' -exec unrar x "{}" \;
```
did nothing :(
```
find . -type f -name '*.rar01'
```
returned nothing :(
Adding sudo to the beginning also did nothing!

As far as directories goes it as so,
/Season-1/episode-1/*.rar01
/Season-1/episode-2/*.rar01
/Season-1/episode-3/*.rar01
/Season-1/episode-4/*.rar01
/Season-1/episode-5/*.rar01

I'm executing this command from /Season-1/ so it finds all the *.rar01 files inside each episode directory.
The command works for *.rar but not *.rar01
I am running Xubuntu 9.10 x64 btw

---

### Post by Teh_Messiah on 2011-02-13
:cry:
I'm a fool!
Sorry for the mess.
file names are /file.part01.rar
Not /file.rar01
Works now that I put this in instead :o
```
find . -type f -name '*01.rar' -exec unrar x "{}" \;
```

---

### Post by Jose Catre-Vandis on 2011-02-13
> **Teh_Messiah said:**
> :cry:
I'm a fool!
Sorry for the mess.
file names are /file.part01.rar
Not /file.rar01
Works now that I put this in instead :o
```
find . -type f -name '*01.rar' -exec unrar x "{}" \;
```


Yes you are a fool :D

Glad you got to the bottom of it, though, and the code works for you. :)

---

### Post by debd on 2011-02-13
it'll be great if someone posts all the commands for unarchieving from the terminal( i mean for diff. formats)

---

