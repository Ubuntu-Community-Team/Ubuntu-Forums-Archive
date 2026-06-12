---
title: "ls with clickable results?"
date: 2011-04-26
forum: General Help
---

### Post by TheHimself on 2011-04-26
I was wondering if there was an enhancement of the ls command such that you could click on each result and it would get opened with the default program. Or if you clicked on a subdirectory you would cd to that directory. Wouldn't this be great?! :)

---

### Post by amauk on 2011-04-26
sounds like you want a console (ncurses based) file manager

try something like Midnight Commander
[http://en.wikipedia.org/wiki/Midnight_Commander](http://en.wikipedia.org/wiki/Midnight_Commander)

---

### Post by TheHimself on 2011-04-26
Well, what I have in mind is much simpler and much more out-of-the-way than midnight commander. Just an enhancement of the ls command. I think it would be useful.

---

### Post by Lateralis on 2011-04-26
Hmmm... not sure I really see the point of this?  If you want clicky-clicky then just navigate to the directory and ensure all of your scripts, codes, files etc. have default programs set.  Else, to open up directories from a terminal window, just type 

```

nautilus [URI]

```

where the URI could be an absolute path in the filesystem or a relative path from the current terminal's working directory.  

To be honest, if you can be bothered to use the keyboard to navigate your way around in a terminal, I don't see why you need to use the mouse.  Am I missing something?  For me, switching between keyboard and mouse slows me down - I can type far quicker than I can manipulate a mouse and single/double click.

---

### Post by trollger on 2011-04-26
Yeah I agrea with the above post, but if you want a nice terminal file browser you can check this post out

[http://www.webupd8.org/2010/02/3-linux-console-file-managers-you.html](http://www.webupd8.org/2010/02/3-linux-console-file-managers-you.html)

---

### Post by Simian Man on 2011-04-26
There is no way to do what you want because terminals have no concept of you clicking on the screen.  You'd have to write your own X11 program to do this.

---

### Post by Arand on 2011-04-26
> **Simian Man said:**
> There is no way to do what you want because terminals have no concept of you clicking on the screen.  You'd have to write your own X11 program to do this.But they do.

- arand

---

### Post by Simian Man on 2011-04-26
> **Arand said:**
> But they do.

- arand

Not across the board they don't.  You can run a terminal without X, or a terminal remotely without X forwarding, also some terminal emulators don't support mouse reporting AFAIK.  I suppose you could support this for some terminals, but not in a general way.

---

### Post by amauk on 2011-04-26
CLI programs can support a mouse
Take a look at GPM (General Purpose Mouse interface)

I've setup links on my Gentoo install with a framebuffer and mouse support for when I (regularly) mess up my X config

*edit*
In fact, here's the Gentoo docs for GPM
[http://www.gentoo.org/doc/en/gpm.xml](http://www.gentoo.org/doc/en/gpm.xml)

---

### Post by TheHimself on 2011-04-27
> **Lateralis said:**
> 
To be honest, if you can be bothered to use the keyboard to navigate your way around in a terminal, I don't see why you need to use the mouse.  Am I missing something?  For me, switching between keyboard and mouse slows me down - I can type far quicker than I can manipulate a mouse and single/double click.

OK, what about using tab  for navigating among the results and return and delete keys for opening( or execution), deletion?

Also I think it is possible for CLI applications to make use of mouse as midnight commnader or aptitude do.

---

### Post by Lateralis on 2011-04-27
> **TheHimself said:**
> OK, what about using tab  for navigating among the results and return and delete keys for opening( or execution), deletion?


To be honest, I'm not trying to stifle innovation and if you want to find a way to do that then go for it!  For me, I use tab completion in conjunction with the name of any relevant programs, e.g. rm, cd, mv, etc...  For regularly used commands or command switches I make aliases.  For more more complicated or repetitive stuff I write small scripts.

As I say though, that's just me, and I certainly wouldn't want to put you off doing more fancy stuff!  Just my two pennies worth, really.

---

