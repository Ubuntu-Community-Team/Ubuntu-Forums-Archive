---
title: "Can somebody teach me how to use screen?"
date: 2006-04-23
forum: General Help
---

### Post by harisund on 2006-04-23
I keep hearing about this screen, how wonderful it is and all that.. what is it? It's man page doesn't seem to help (too technical I think for me) 

What is it primarily used for? How does it help me? ( I primarly SSH into my Linux box at home from my school, where I am all day without access to Linux) Can it work through SSH? 

Thanks !

---

### Post by sinkxdie on 2006-04-23
What "screen?"
Is it an app?
Im confused...what do you mean by screen?

---

### Post by dermotti on 2006-04-23
Lol, yea what is **screen**?

---

### Post by sinkxdie on 2006-04-23
Lol, yeah and there's not really any point to googling "screen"

---

### Post by dermotti on 2006-04-23
You should call it **GNU Screen** if you want help

[http://en.wikipedia.org/wiki/GNU_Screen](http://en.wikipedia.org/wiki/GNU_Screen)

---

### Post by sinkxdie on 2006-04-23
Hah, I guess that's what he was talking about.
And where do you keep hearing about it?

[http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/)

Thats the homepage

---

### Post by dermotti on 2006-04-23
EDIT: looks like command line only.

---

### Post by Zorro on 2006-04-23
screen starts a shell session that runs in the background, thus it can be closed down and it still runs, unlike a regular session.

I operate my bittorrent session in a screen session. SO what I can do is, when I get to work, I ssh into my box from work I then screen -r and it attaches the shell session and I can use bt from work ;).. but this can be used for any shell based app...

---

### Post by sinkxdie on 2006-04-23
[ftp://ftp.gnu.org/gnu/screen/](ftp://ftp.gnu.org/gnu/screen/)

And that would be where to obtain it...

---

### Post by harisund on 2006-04-23
The software application screen
```
man screen
```
screen - screen manager with VT100/ANSI terminal emulation
Screen is a full-screen window manager that multiplexes a physical terâ
       minal between several processes (typically interactive  shells).   Each
       virtual terminal provides the functions of a DEC VT100 terminal and, in
       addition, several control functions from the ISO 6429  (ECMA  48,  ANSI
       X3.64)  and ISO 2022 standards (e.g. insert/delete line and support for
       multiple character sets).  There is a  scrollback  history  buffer  for
       each virtual terminal and a copy-and-paste mechanism that allows moving
       text regions between windows.

---

### Post by sinkxdie on 2006-04-23
Based on what zorro said you should be able too.

---

### Post by dermotti on 2006-04-23
sinkxdie, its "You - Buhn - too"

---

### Post by sinkxdie on 2006-04-23
How do you people know these things?
Now I have no signature anymore :(

---

### Post by cjazz on 2006-04-23
[QUOTE=dermotti]sinkxdie, its "You - Buhn - too"[/QUOTE]

Pronouncing "u" as "you" is, as far as I know, an English-speaking trait. But ubuntu is a word from the Zulu and Xhosa languages. In any case, according to [this FAQ](http://www.ubuntu.com/support/faq?action=show&redirect=FAQ), sinkxdie has it right.

---

### Post by kabus on 2006-04-23
Beginner's tutorials :
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)
[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

the fine manual :
[http://www.delorie.com/gnu/docs/screen/screen_toc.html](http://www.delorie.com/gnu/docs/screen/screen_toc.html)

screen users mailing list :
[http://lists.gnu.org/archive/html/screen-users/](http://lists.gnu.org/archive/html/screen-users/)

some cool config examples :
[http://phraktured.net/gnu-screen/](http://phraktured.net/gnu-screen/)
[http://bbs.archlinux.org/viewtopic.php?t=20803&highlight=screen+configuration](http://bbs.archlinux.org/viewtopic.php?t=20803&highlight=screen+configuration)

some stuff you'll probably want in your ~/.screenrc :

```
# Don't display the copyright page
startup_message off

# No annoying audible bell, using "visual bell"
vbell on        # default: off
vbell_msg ""

# don't kill screens after the process dies
zombie "kr"

# Change to left/right window in relation to current window
# (wraps on edges) ALT-,.
bindkey "^[," prev
bindkey "^[." next
```

> [ftp://ftp.gnu.org/gnu/screen/](ftp://ftp.gnu.org/gnu/screen/)

And that would be where to obtain it...

You can simply apt-get it.

---

### Post by harisund on 2006-04-23
Perfect. Thanks !

---

### Post by sinkxdie on 2006-04-23
Ok cjazz, but dermotti still killed my sig :D

---

