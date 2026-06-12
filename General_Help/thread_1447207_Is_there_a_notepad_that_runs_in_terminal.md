---
title: "Is there a notepad that runs in terminal"
date: 2010-04-05
forum: General Help
---

### Post by spiky001 on 2010-04-05
I,m looking for a notepad type that runs in terminal? i,e when I (ctlr alt f1) I have terminal can you run a notepad within that, or is there a way to type something then be able to save etc

---

### Post by NightwishFan on 2010-04-05
Yes indeed! I like Nano. It is already installed.
```
nano filename
```

---

### Post by Dayofswords on 2010-04-05
i believe vi is the built in text editor in linux

there is vim though

(guessing here)

---

### Post by underquark on 2010-04-05
Not sure exactly what you're after but would this do?
(Places a text editor button on your panel):

Right-click on panel
Add to Panel
Application Launcher
-> Forward button
Click on the -> arrow to expand Accesories
Choose Text Editor

---

### Post by sheperson on 2010-04-05
> **Dayofswords said:**
> i believe vi is the built in text editor in linux

there is vim though

(guessing here)
Well I think vim is a perfect solution too. 
It's a wonderful beast.

---

### Post by spiky001 on 2010-04-05
OK ta I dont have vim installed but not a problem nano is there, only ! thing I couldn't find how you save in nano found my way around help folders etc just saving

---

### Post by NightwishFan on 2010-04-05
Press ctrl+x to save a file.

---

### Post by ad_267 on 2010-04-05
Vi/Vim isn't a good idea if you just want a simple text editor. It's very powerful but also has a bit of a learning curve and is more for computer programmers. Nano is a good simple text editor and is most likely what you want. If you do want to learn vim you can install it with "sudo apt-get install vim" and run the command "vimtutor" to find out how to use vim.

When you first run nano there should be a list of commands at the bottom that tell you how to do stuff. The "^" symbol means the ctrl key, so "^O WriteOut" means press ctrl+O to write (save) the file you're editing.

---

### Post by spiky001 on 2010-04-05
I have done that then it gives option for title & where to save, if you ctlr x it asks again to save? But no actual save

---

### Post by ad_267 on 2010-04-05
Why do you say there's no actual save? Do you get any errors?

---

### Post by wojox on 2010-04-05
Ctrl+o saves 

Ctrl+x exits

---

### Post by NightwishFan on 2010-04-05
My mistake. ](*,)

I normally just edit pre-existing files and ctrl+x gives me an option to save them.

---

### Post by spiky001 on 2010-04-05
I think I got that, so can you create a new document then save to specific location?

---

### Post by oldos2er on 2010-04-05
[https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

To create a new text file, run **nano /home/user/newfile**. To create a new text file outside your home directory, you'll need sudo: **sudo nano /etc/somefile.cfg**, for example.

---

### Post by KeyserSoze93 on 2010-04-05
Recently, I constructed a script which sets the system up to do just this.

It loads an instance of nano, which runs on TTY10 (ctrl-alt-f10), automatically, when the system is booted.

I'll put it on my website, here:

[http://tpn.lowtech.org/scripts/mk_tech_log.sh]("http://tpn.lowtech.org/scripts/mk_tech_log.sh")

You'll need to edit it to choose which file to edit, etc,

---

### Post by spiky001 on 2010-04-05
Ok so i followed oldos2er still didn't work so I created a file then opened it nano /home/user/Documents/test.txt

I then added some more to it tried to save that way
It returns no file?

OK my fault as this was my 1st attempt at using nano I found my mistake I wasn't putting the save route correctly
THKS to all

---

