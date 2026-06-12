---
title: "How to adjust colors in Terminal for files, folders, links,...?"
date: 2009-10-22
forum: General Help
---

### Post by pstein on 2009-10-22
When I open a Terminal and type 
 
ls -la
 
then different of objects appear:
 
Files, folders, links, .....
 
All of them have different colors.
 
How can I adjust these color or turn them all into black?
 
Peter

---

### Post by 80aless on 2009-10-22
I would first look in your ~/.bashrc file. maybe you have an alias as:
```
alias ls='ls --color=auto'. 
```
comment it and see if everything turns black. the default colors must be in:
/usr/bin/dircolors
```
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
```
but i do not know how to modify them

---

### Post by uncle-c on 2009-10-22
If you want to configure Xterm then you can edit / create a file called .Xresources and place all your xterm settings in there.

[http://kb.mit.edu/confluence/pages/viewpage.action?pageId=3907291]("http://kb.mit.edu/confluence/pages/viewpage.action?pageId=3907291")

---

### Post by P4man on 2009-10-22
You guys make it so hard.
just go edit / profile preferences / colors.

select a custom scheme and make all colors white or shades of grey or whatever you want.

---

### Post by geirha on 2009-10-22
This will save a file (mydircolors) with the default colors
```
dircolors --print-database > mydircolors
```
The format is explained in comment fields in the file. Edit it to your liking, then run
```
eval "$(dircolors mydircolors)"
```
to load them. If you want to have those colors every time, edit ~/.bashrc, search for dircolors and add your file to the end of the dircolors command.

---

### Post by schezel2000 on 2010-04-22
I can change my background color and text color but i want the ls command to have color coding based on whether or not the object is a directory or a file etc. If i use the ls command everything shows up as my selected text color.

---

### Post by geirha on 2010-04-22
The default .bashrc has an alias for that. What does **type ls** say? Running **ls --color=auto** should colorize output based on filetype and extension, but only if the output is going to a terminal.

---

