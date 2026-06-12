---
title: "Having trouble compiling"
date: 2006-02-10
forum: General Help
---

### Post by Piggah on 2006-02-10
Hi,

I recently downloaded gnuski, and the only option to install was to compile from source. In the readme file it said that to compile it, I needed to do this: 
```
c++ -O2 -o gnuski.o main.cpp -lncurses -lpthread
```

However, when I run that command I get this and am unable to compile:

> nick@nick:~/Desktop/gnuski-0.2$ c++ -O2 -o gnuski.o main.cpp -lncurses -lpthread
main.cpp:7:44: error: curses.h: No such file or directory
init.h: In function ‘void init_colors()’:
init.h:19: error: ‘start_color’ was not declared in this scope
init.h:21: error: ‘COLOR_BLACK’ was not declared in this scope
init.h:21: error: ‘init_pair’ was not declared in this scope
init.h:22: error: ‘COLOR_GREEN’ was not declared in this scope
init.h:23: error: ‘COLOR_RED’ was not declared in this scope
init.h:24: error: ‘COLOR_CYAN’ was not declared in this scope
init.h:25: error: ‘COLOR_WHITE’ was not declared in this scope
init.h:26: error: ‘COLOR_MAGENTA’ was not declared in this scope
init.h:27: error: ‘COLOR_BLUE’ was not declared in this scope
init.h:28: error: ‘COLOR_YELLOW’ was not declared in this scope
init.h: At global scope:
init.h:31: error: expected constructor, destructor, or type conversion before ‘*’ tokeninit.h: In function ‘void finish(int)’:
init.h:48: error: ‘endwin’ was not declared in this scope
init.h:50: error: ‘echo’ was not declared in this scope
draw.h: In function ‘void add(int, int, char)’:
draw.h:23: error: ‘move’ was not declared in this scope
draw.h:24: error: ‘addch’ was not declared in this scope
draw.h: In member function ‘virtual void skiDude::draw()’:
draw.h:144: error: ‘COLOR_CYAN’ was not declared in this scope
draw.h:144: error: ‘color_set’ was not declared in this scope
draw.h:162: error: ‘COLOR_WHITE’ was not declared in this scope
draw.h: In member function ‘virtual void tree::draw()’:
draw.h:189: error: ‘COLOR_GREEN’ was not declared in this scope
draw.h:189: error: ‘color_set’ was not declared in this scope
draw.h:192: error: ‘COLOR_YELLOW’ was not declared in this scope
draw.h:194: error: ‘COLOR_WHITE’ was not declared in this scope
draw.h: In member function ‘virtual void rock::draw()’:
draw.h:219: error: ‘COLOR_WHITE’ was not declared in this scope
draw.h:219: error: ‘color_set’ was not declared in this scope
main.cpp: In function ‘int main(int, char**)’:
main.cpp:30: error: ‘WINDOW’ was not declared in this scope
main.cpp:30: error: ‘wnd’ was not declared in this scope
main.cpp:30: error: ‘initStuff’ was not declared in this scope
main.cpp:48: error: ‘clear’ was not declared in this scope
main.cpp:54: error: ‘refresh’ was not declared in this scope
main.cpp:62: error: ‘getch’ was not declared in this scope
main.cpp:65: error: ‘KEY_UP’ was not declared in this scope
main.cpp:66: error: ‘KEY_DOWN’ was not declared in this scope
main.cpp:67: error: ‘KEY_RIGHT’ was not declared in this scope


Most of that is just jibberish to me, so I'm pretty much lost. 

If anyone could explain to me how I would go about compiling that or if there's  anything that I need to do so, I'd really appreciate it.

Thanks in advance.

---

### Post by dcstar on 2006-02-10
[QUOTE=Piggah]Hi,

I recently downloaded gnuski, and the only option to install was to compile from source. In the readme file it said that to compile it, I needed to do this: 
```
c++ -O2 -o gnuski.o main.cpp **-lncurses -lpthread**
```

However, when I run that command I get this and am unable to compile:
.......[/QUOTE]
You probably need the ncurses and pthread libraries installed on your system, search for them in Synaptic and see if things change.

---

### Post by Piggah on 2006-02-10
I can't seem to find either of those..

---

### Post by dcstar on 2006-02-10
[QUOTE=Piggah]I can't seem to find either of those..[/QUOTE]
You may have to enable **all** the repositories on your system, do a search for the HOWTO on this.

Various ncurses packages are certainly available, the pthread isn't on my system so it may be there anyway.

PS, if your are compiling things ,you need the -dev packages.

---

### Post by Piggah on 2006-02-10
I'm still unable to find anything. 

edit: What -dev packages do I need? =\

---

