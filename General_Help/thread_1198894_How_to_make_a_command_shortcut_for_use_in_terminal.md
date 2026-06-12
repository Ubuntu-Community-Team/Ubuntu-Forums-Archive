---
title: "How to make a command shortcut for use in terminals?"
date: 2009-06-28
forum: General Help
---

### Post by alcatraz678 on 2009-06-28
Hi guys, I know that you feel the same way as I do. it's hard to type the commands especially long commands in the terminal.. I'm still a terminal newbie but I want to learn how to make a shortcut for all the commands that i use often. For example, how can I transform this line:
```
/opt/lampp/lampp/start
```

into this:
```
start
```

That's just a general example.. I know it's possible because I saw it somewhere but I couldn't remember where..

Thanks!!

---

### Post by anystupidname on 2009-06-28
alias start='/opt/lampp/lampp/start'

you'll have to add aliases to ~/.profile if you want them to be persistent

---

### Post by Nythain on 2009-06-28
well, if you dont already have a "start" command in your path, you could either

A. add a link to the executable in your path... sudo ln /opt/lampp/lampp/start /usr/bin/start
or
B. create an alias in your shells config file... alias start="/opt/lampp/lampp/start" or something to that effect

there's probably other ways, but those are the two i would use myself

---

### Post by kilowattradio on 2009-06-28
You can use shell scripting or symbolic linking. It all depends what you prefer. 

```

cd ~
mkdir bin
ln -s /opt/lampp/lampp/start bin/start


```
or you can put the link in any bin directory

```

sudo ln -s /opt/lampp/lampp/start /usr/local/bin/start


```
If you want to use shell scripting you create a file lets say 
it is *startlamp.sh*
gedit startlamp.sh
```

#!/bin/bash
exec /opt/lampp/lampp/start

```
save to your $HOME/bin directory and run from there.

 If you need to add more data to start the program you can easily learn about shell scripting at many web sites via google. I think for your purposes a symbolic link will do the job. 
:P

---

### Post by kabeza on 2010-03-03
Hi guys...
Is there any way to add a shortcut into the desktop for starting xampp? I guess the sh files, etc. are stored in other folder rather than desktop...

---

### Post by methodtwo on 2010-03-03
> **kabeza said:**
> Hi guys...
Is there any way to add a shortcut into the desktop for starting xampp? I guess the sh files, etc. are stored in other folder rather than desktop...

Hola Kabeza. Terminal = command line interface.
Find it at Applications - Accessories - Terminal.
To put an icon launcher on the gnome desktop:
Right-click on the desktop.
Select 'Create Launcher'.
Fill in the blanks!

---

