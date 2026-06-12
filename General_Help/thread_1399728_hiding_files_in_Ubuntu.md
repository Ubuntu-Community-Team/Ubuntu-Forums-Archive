---
title: "hiding files in Ubuntu"
date: 2010-02-06
forum: General Help
---

### Post by pranavk_uict on 2010-02-06
I am a new user of Ubuntu. Just installed it for fun, and now use ubuntu half the time.
I use windows 7 as the other operating system. In my music folder, I have huge number of jpg images which are generated to display album art in windows media player 12. In windows, these files are hidden, but in ubuntu, it becomes a headache for browsing as these files are shown always. I want to hide all these image files in ubuntu. Can someone suggest me a way by which I can hide all these image file in my music folder at once. It is too boring to do it manually for each file...
Thanks in advance...

---

### Post by mushwars on 2010-02-06
```
for i in *.gif; do mv -i "$i" ".$i"; done
```I havent tested it, but that should move all the .gif images so like album.gif and put a . infront of it so .album.gif which will hide it.

let me do a quick test before you try it though.

[s]Carefull with that command, I accidently just deleted **ALL** my gif picture when editing it, right now it doesnt delete them but its still not right, let me do some more tests.[/s]
:D
good I didnt delete them my trick works it will seriously hide them and you wont even know you have them. a simple ls -al showed me they were still there. 

so do this for all the picture file extentions...

```
for i in *.gif; do mv -i "$i" ".$i"; done
```

grumble. now I need a command to undo it >_<

---

### Post by mushwars on 2010-02-06
anyone have an idea to make that recursive?

I have been doing some thinking but I guess the op has like say 100 artists and 2 albums each he would have to run the command 200 times.

I am also curious on how to make that recursive.

you would have to do foreach or forall and then specify folders, but this is not my expertise of programming. Maybe if I whip something up in python.

---

