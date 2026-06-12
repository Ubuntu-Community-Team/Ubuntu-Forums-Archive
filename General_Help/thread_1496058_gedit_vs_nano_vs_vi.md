---
title: "gedit vs nano vs vi"
date: 2010-05-28
forum: General Help
---

### Post by TideMan on 2010-05-28
I have noticed that quite a few tutorials suggest using nano or vi to edit text files.  These editors are awful.  They remind me of WordMaster that we used to use back in the 1980s with CP/M systems when hard disks did not exist and we ran off two 7" floppy disks using 64K of memory.

I have been wondering why anyone would use such archaic editors when gedit is available?  And to recommend that learners use such editors seems weird.

Perhaps there's a good reason?

---

### Post by Joe of loath on 2010-05-28
Although gedit is easier to use, vi is HUGELY more powerful. Personally I prefer nano though, it makes a 'quick edit' much quicker by doing it all in the terminal. I also find it easier to use than gedit, but that's personal preference.

---

### Post by Snow986 on 2010-05-28
gedit is a gnome program.  vim (vi), emacs, and nano are all available through command line and are very minimal.  You could try emacs.  It has X11 and terminal views.  I prefer gedit for coding but I work on SLC5 servers that have only X11 so emacs and vim are best suited for working in these types of environment.

---

### Post by blur xc on 2010-05-28
Other than vim being extremely powerful, it's also available by default on just about every unix system.  Gedit is nice, but what do you do when your gui breaks and you need to edit a config file in the terminal?  If you don't know how to use a good command line text editor - you'll be in for a lot more work.  The next easiest thing to do would be to boot up into a live cd, mount the partition w/ the config files, and then use gedit- or you could just learn vim.  It's not that hard once you learn a few commands, and they say you will start being productive once you learn about 20 commands or more...

BM

---

### Post by TideMan on 2010-05-28
Odd sort of argument that.
It's like saying you should use a bicycle, not a car, because a bike can go lots of places a car cannot go and what will happen if your car breaks down?  You will have no way of getting home.  Whereas, if you used a bicycle, you'd never have to worry about that.

If my GUI breaks, I'm screwed, so I think I'll stick with gedit.

---

### Post by Spiritof76 on 2010-05-28
> **TideMan said:**
> Odd sort of argument that.
It's like saying you should use a bicycle, not a car, because a bike can go lots of places a car cannot go and what will happen if your car breaks down?  You will have no way of getting home.  Whereas, if you used a bicycle, you'd never have to worry about that.

If my GUI breaks, I'm screwed, so I think I'll stick with gedit.
I probably use gedit more than I use vi(M) but VI or nano are very useful when one find oneself buried in the command mode, and deep into the the sub-directory structures. 

Sometimes a Table saw is best. other times a coping saw works best.  Different tools for different situations. A couple hours is all it takes to learn enough to be comfortable with VI(m).

---

### Post by vashman on 2010-08-05
Well if its a matter of the interface vi or vim has some available and are quite cool. Nano is sort of just a TUI(terminal user interface). This gets trumped if your using a GUI in a manner of speaking.

The only thing I have a problem with using GVim interface is I have not found the correct way to use bi-directional text. Either way I am leaning toward vi because it's there for the terminal, and the gui comes in handy when someone else needs a text editor which in terms saves space and management.
The only advantage that nano has that its kind of quick with its meta chords in a command line interface. The interface is usually what it comes down to for most people over the underlying architecture of the program.

---

### Post by pipemartinm on 2010-08-05
> **TideMan said:**
> If my GUI breaks, I'm screwed, so I think I'll stick with gedit.
Ubuntu server edition ships without the GUI installed. Vim is a very good editor for CLI environments.  If using people using Vi is the most archaic thing you see consider yourself lucky. I work with people who still use tar as their package manager :D.

---

### Post by satanenterprises on 2011-04-16
I'm having to learn vi to work on linux based servers remotely.
 
After quite a lot of use I am not convinced, I think people like the feeling of mastering commands and knowing all elite tricks to the program but I think the actual productivity increases are questionable. I would love to see a study on users of these editors over the long run.
 
In other editors people are already making use of the most common shortcuts like ctrl-f, tabbing fields and ctrl-s while being able to click/drag (double/tripple click) exactly where they want to type/select rather than the often very long key combos.

---

### Post by Thewhistlingwind on 2011-04-16
> **satanenterprises said:**
> I'm having to learn vi to work on linux based servers remotely.
 
After quite a lot of use I am not convinced, I think people like the feeling of mastering commands and knowing all elite tricks to the program but I think the actual productivity increases are questionable. I would love to see a study on users of these editors over the long run.
 
In other editors people are already making use of the most common shortcuts like ctrl-f, tabbing fields and ctrl-s while being able to click/drag (double/tripple click) exactly where they want to type/select rather than the often very long key combos.

Emacs runs in X, though I wouldn't necessarily recommend it.

---

### Post by idoitprone on 2011-04-16
OP please dont bash(lol pun) other editors. The greatest thing about vi is also the worst thing about it. There is a command or keystroke for everything which raises the learning curve. If you use it enough, the experience is not so bad. In fact, it it consider the fastest text editor along side emacs.

As sataneterprises mention, vi can be quite confusing for first time user

However i do not see you argument to be valid on productivity. Vi is just a different approach. 

/findstring

then press n for next or shift+n to find previous

:wq

save and quit



cut, copy and paste is when i miss a mouse

one y to cut another one to yy
v then move around
y cut
yy copy

p for paste

seems to me that you need more practice to get it right

> Emacs runs in X, though I wouldn't necessarily recommend it.This reminds me of a joke "Emacs a great operating system that lacks a good text editor." Ahhhh, flames wars  are funny

---

### Post by Zwany on 2011-04-17
Learn vi if you can, its harder to name distros that don't have it, than do:popcorn:

---

### Post by yetiman64 on 2011-04-17
> **idoitprone said:**
> OP please dont bash(lol pun) other editors....

The OP hasn't posted on this thread since the 29th May 2010 (11 months ago) or this site since 18th February 2011, may be a while before he sees the pun ;). 

This thread was resurrected ~55 minutes ago from an 8 month sleep. 

Not too bad a pun that one though :).

Edit: Very good tutorial linked in post 14 below for vi/vim.

---

### Post by Blasphemist on 2011-04-17
For someone that isn't as old as us and can't imagine why we'd use VI/VIM, check out this video from lullabot and watch a good user teach its use. [http://www.lullabot.com/videos/command-line-basics-more-editing-with-vivim](http://www.lullabot.com/videos/command-line-basics-more-editing-with-vivim)

---

### Post by Elfy on 2011-04-17
closed

---

