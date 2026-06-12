---
title: "strange package"
date: 2010-09-23
forum: General Help
---

### Post by salmonila on 2010-09-23
hi ,I downloaded marvin sketch as an alternative for chemdraw,but the linux package has a(.sh) extension which I can't open with package manager, can any one help?

---

### Post by WorMzy on 2010-09-23
That file is a shell script. Presumably you run that to install it. Check the readme if there is one.

---

### Post by lfforman on 2010-09-23
I am not an expert but a .sh is a shell script you basically need to run it in a terminal.

normally in those cases you will find a readme file were they explain the proper way you need to run it

when i find those files i do the following

1 - open a terminal
2 - type: sudo ./filename.sh

this will run the file and make it do what is need to be done.

I would suggest for you to google for some support and how to malke it work in the right way

---

### Post by CharlesA on 2010-09-23
There are install inscructions here:

[http://www.chemaxon.com/marvin/help/applications/install.html#install_linux](http://www.chemaxon.com/marvin/help/applications/install.html#install_linux)

Basically they just want you to run the shell script. You need to have java installed as well.

---

### Post by salmonila on 2010-09-23
thank you,and sorry for being a newpy

---

### Post by CharlesA on 2010-09-23
No need to apologize. :)

Just mark the thread as solved from the thread tools.

---

### Post by salmonila on 2010-09-23
sorry but am not any good at command lines ,can any one tell me what I did wrong?
(the installer is in the home folder)
[IMG]http://img841.imageshack.us/img841/1220/screenshot1x.png[/IMG]
[IMG]http://img163.imageshack.us/img163/9894/screenshot2id.png[/IMG]

---

### Post by WorMzy on 2010-09-23
You put a " at the start of the cd command, making the shell think it's receiving a string; it's waiting for the other ", which signifies the end of the string.

Press Ctrl+C to cancel that, because it'll just result in an error once it gets the second " anyway, and then re-enter the commands without the ". Also, leave a space between the cd and the directory, otherwise the shell will think you're trying to run a command called "cd~/home/mohammed", which doesn't exist. Finally, that directory doesn't exist. "~" expands to the path to your home directory, so you don't need the "/home/mohammed" after it.

so:

```
cd ~/
sudo sh marvinbeans-VERSION-linux.sh
```

Note that sh might not work. You may need to use bash instead. Also, you don't actually need the cd command in this instance. You are already in your home folder (It says your current directory after the "mohammed@mohammed-laptop:", in this case you're already in ~, which, as I already said, is your home folder.)

---

### Post by CharlesA on 2010-09-23
You had a quotation mark at the start of the line.

When you open a new terminal it defaults to yer home directory.

Just type:

sudo ./marvinbeans-5.3.8-linux.sh

---

### Post by salmonila on 2010-09-23
you where right it couldn't run this version of the file,so what will be the bash command

---

### Post by CharlesA on 2010-09-23
Make sure it has execute permission:

```
chmod +x marvinbeans-5.3.8-linux.sh
sudo ./marvinbeans-5.3.8-linux.sh
```

---

### Post by WorMzy on 2010-09-23
Charles' way of running the file is probably the best way to run the script, assuming that it has a shebang ("#!/bin/something" at the top of the file), it will automatically launch the correct shell for the script.

To run the command with bash instead of sh, just the change the sh at the start of the command to bash:

```
sudo sh marvinbeans-5.3.8-linux.sh
```

(Note that in my previous post, I made the mistake of copying the file name from your terminal screenshot, which was the incorrect name and may be the reason why the script didn't run).

---

