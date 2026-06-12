---
title: "gaming"
date: 2010-07-08
forum: General Help
---

### Post by supertails on 2010-07-08
I'd like to make a text-based adventure game but I don't know the first thing about programming. Can u help me?

---

### Post by Devi1903 on 2010-07-08
Hint: Learn some programming

---

### Post by supertails on 2010-07-08
That's obvious.

---

### Post by qamelian on 2010-07-08
Check out TADS. It's in the repos. I don't know what shape its in now, but I used to use it and play games written for it years ago on the Atari ST. The documentation is in the repos, as well.
```
carl@arkham:~$ apt-cache search tads
gargoyle-free - graphical player for Interactive Fiction games
qtads - Qt text-only interpreter for TADS
tads2-mode - Emacs mode for editing TADS code
tads2 - Text mode interpreter for TADS version 2 game files
tads2-dev - TADS version 2 development tools
tads3 - Text mode interpreter for TADS game files
tads3-dev - TADS version 3 development tools
tads3-doc - TADS version 3 documentation

```

---

### Post by supertails on 2010-07-08
Would I have to worry about graphics cause all I'm looking for is. "You went into a castle. You see a scary looking door in front of you, a dark room to your right, and a very rare gem stone."

I enter "get gem stone"

"You trigger a trap door and you fall to your death"

or I enter "enter door"

"You see a very scary man holding an sword, covered in armor. He's walking towards you"

or I enter "go right"

"You enter the dark room and can't see a thing"

Something like that.

---

### Post by RMuscaritolo on 2010-07-08
Sounds like simple if/then/else/elif kinda programing...

The truth is, this sounds like a very simple form of programing and I'm sure most, if not all, programming languages are going to start you off at this very level.

I would first start with BASH scripting, this would help not only with writing your game, but also help with system administration (if you're in that kind of thing).

Otherwise, why not try Python. I hear that is fast becoming the most popular scripting language?

Go ahead and search for some quick tutorials online and they should all cover your "if users types this, then do that" statements. 

Good Luck!

---

### Post by s.fox on 2010-07-08
Hello,

If you wish to learn Python to build your game I recommend [A Byte of Python]("http://www.cesarkallas.net/arquivos/apostilas/python/doc/byteofpython_120.pdf").  Very good free book for you to download in pdf format.

-Silver Fox

---

### Post by BurningSludge on 2010-07-08
[FONT=Comic Sans MS][SIZE=3]You could go to [http://freecomputerbooks.com/](http://freecomputerbooks.com/) or [http://www.onlinecomputerbooks.com/](http://www.onlinecomputerbooks.com/)[/SIZE][/FONT][SIZE=3] and brows for free ebooks on programming there.[/SIZE]

---

### Post by supertails on 2010-07-08
Can u fix it?
[PHP]print "Welcome to Fire of Demons, I hope you will love the game."
print "It starts out in modern times but it dates"
print "back 10 years ago. When all were"
print "happy but The Dark King hated it and decided to make demons"
print "The demons slowly started taking over the world."
print "One brave fox named Sam. Will try to stop the"
print "demons from taking over the world."
print "Can he destroy all the demons? I hope so."

print "You are on the Mansion Grounds. You married into money"
print "and everything is good and calm here"
print ""
print "1.) Enter your Mansion"
print "2.) Go East"
print "3.) Go West"
print "4.) Go South"
x = int

if x == "1" then_goto Mansion
if x == "2" then_goto East
if x == "3" then_goto West
if x == "4" then_goto South

Mansion:
els
print "You are in your Mansion. You see a Staircase going up"
print "Two rooms East and West. A room pass the Stairs"
print ""
print "1.) Go Up"
print "2.) Go East"
print "3.) Go West"
print "4.) Go South"
print "5.) Pass Stairs"
x = int

if x == "1" then_goto Up
if x == "2" then_goto East
if x == "3" then_goto West
if x == "4" then_goto South
if x == "5" then_goto Pass

East:
els
West:
els
South:
els[/PHP]

---

### Post by BurningSludge on 2010-07-08
> **supertails said:**
> Can u fix it?
[PHP]print "Welcome to Fire of Demons, I hope you will love the game."
print "It starts out in modern times but it dates"
print "back 10 years ago. When all were"
print "happy but The Dark King hated it and decided to make demons"
print "The demons slowly started taking over the world."
print "One brave fox named Sam. Will try to stop the"
print "demons from taking over the world."
print "Can he destroy all the demons? I hope so."

print "You are on the Mansion Grounds. You married into money"
print "and everything is good and calm here"
print ""
print "1.) Enter your Mansion"
print "2.) Go East"
print "3.) Go West"
print "4.) Go South"
x = int

if x == "1" then_goto Mansion
if x == "2" then_goto East
if x == "3" then_goto West
if x == "4" then_goto South

Mansion:
els
print "You are in your Mansion. You see a Staircase going up"
print "Two rooms East and West. A room pass the Stairs"
print ""
print "1.) Go Up"
print "2.) Go East"
print "3.) Go West"
print "4.) Go South"
print "5.) Pass Stairs"
x = int

if x == "1" then_goto Up
if x == "2" then_goto East
if x == "3" then_goto West
if x == "4" then_goto South
if x == "5" then_goto Pass

East:
els
West:
els
South:
els[/PHP]

[FONT=Comic Sans MS][SIZE=3]What makes you think I know how to program?  :confused: Go to [launchpad.net]("https://launchpad.net/").[/SIZE][/FONT]

---

### Post by farvardin on 2010-08-03
Inform7 is easy to use for creating adventure games. For installing it, there is a deb on the website:

[http://inform7.com/](http://inform7.com/)

If you prefer a CYOA style, then use Renpy, it's also easy to use and well designed: [http://www.renpy.org/](http://www.renpy.org/)

Both of them will give you more fun for creating a game than bash or php.

---

