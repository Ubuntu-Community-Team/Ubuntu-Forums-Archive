---
title: "Run Change Directory and Wget without a terminal?"
date: 2009-11-11
forum: General Help
---

### Post by AldenIsZen on 2009-11-11
I am trying to get my wallpaper to switch on it's own from a website. I am using gnome-schedule so that I don't have to get confused by all of the cron commands just yet. The issue I am running into is tha ta terminal window is opened. I suppose that I could just add add an "exit" command, but I would rather not have the terminal window pop-up at all. Is there a way to fix the command below to not open the terminal, yet run the commands?

```
cd /usr/share/backgrounds && wget http://static.die.net/earth/rectangular/1440.jpg
```

---

### Post by sisco311 on 2009-11-11
```
wget -O /usr/share/backgrounds/1440.jpg http://static.die.net/earth/rectangular/1440.jpg
```

---

### Post by AldenIsZen on 2009-11-11
Unfortunately I still got the terminal window. I now have the code as below, otherwise I was getting multiple images, instead of them being overwritten.

edit/
```
cd /usr/share/backgrounds && rm 1440.jpg; wget http://static.die.net/earth/rectangular/1440.jpg && exit
```

This seems to work, at least when ran automatically. I am not sure if I need the exit, but it is there. I am currently learning to program ruby, so I will make something a little better.

---

