---
title: "Terminal Commands"
date: 2012-02-16
forum: General Help
---

### Post by PadiSka on 2012-02-16
How do I open a file with terminal? Or launch an application. Like for an example if I wanted to open a music file with banshee just to see if I had the right file, how would I do it in terminal?

Or can you only use terminal based apps like gedit?

---

### Post by haqking on 2012-02-16
> **PadiSka said:**
> How do I open a file with terminal? Or launch an application. Like for an example if I wanted to open a music file with banshee just to see if I had the right file, how would I do it in terminal?

Or can you only use terminal based apps like gedit?

well depends on the application or file.

for an application you usuully just type its name or alias.

second gedit is not a terminal based app it is a graphical app.

---

### Post by PadiSka on 2012-02-16
I didn't mean gedit was a CLI based app I was only using the word "based" to convey that it was an app accessible from terminal as my question reflected that I didnt know that all apps were accessible from terminal. 

So how would one open a music file with banshee?

---

### Post by wolfen69 on 2012-02-16
> **PadiSka said:**
> 
So how would one open a music file with banshee?

```
banshee /path/to/music-file.mp3
```

examples:
```
banshee /home/wolfen69/Music/crazy-train.mp3
```
the same thing can be shortened to
```
banshee ~/Music/crazy-train.mp3
```

---

### Post by Khayyam on 2012-02-17
If you install [xdg-utils]("http://portland.freedesktop.org/wiki/") you can use the command [xdg-open]("http://portland.freedesktop.org/xdg-utils-1.0/xdg-open.html") to open files (and URL's) based on its type and your prefered application.

```
apt-get install xdg-utils
```use ...

```
xdg-open file.mp3
```HTH ...

---

