---
title: "autorun.inf virus on mp3"
date: 2010-06-24
forum: General Help
---

### Post by mastodon1314 on 2010-06-24
hey 

im new in ubuntu and i have a virus in my mp3 that i don't know how to get rid of. 
the virus is called 'autorun.inf'. 
even though it doesn't affect Linux (i think) when i mount the mp3, the icon appears as if it was an empty folder. it use to let me delete/copy files into the mp3 but now it doesn't anymore. i cant delete the autorun.inf file or any file! 

Ive had this problem before on the same mp3 and what i did was format the mp3 in windows but the thing keeps coming again and again .:confused:
ive seen a couple 'windows solutions' for this but i dont have windows anymore so...

how to i solve this and keep it from happening again??

PLEASE HELP!!! thanks

---

### Post by ajgreeny on 2010-06-24
I assume you mean the virus is on your mp3 player, not actually on an mp3 file.  If I am right there is a host of info on a quick google search, which I have not gone too deeply into, but it looks as if it is well known and can be removed, though there is also some doubt about whether it really is a virus or not.

Check out [http://www.google.co.uk/search?q=autorun.inf+virus&ie=UTF-8](http://www.google.co.uk/search?q=autorun.inf+virus&ie=UTF-8) for lots of info, which I will have to let you search yourself.

**autorun.inf** is a perfectly normal file on many media sources, eg CDs, DVDs, simply telling windows what to do with the disk when it is loaded into a windows computer.

---

### Post by kiddykoff on 2010-07-17
you could probably try using sudo to remove it. change the directory to mp3 first then run.

```
sudo rm autorun.inf
```

---

### Post by Penguin Guy on 2010-07-17
There's a simple command to 'vaccinate' your mp3:
```
cd /media/**mp3**
echo caacaacaacaacaa > AUTORUN.INF
```
(replace **mp3** with the filename of your mp3)

---

