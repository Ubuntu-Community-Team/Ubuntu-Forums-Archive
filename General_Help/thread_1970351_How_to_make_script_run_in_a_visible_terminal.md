---
title: "How to make script run in a visible terminal?"
date: 2012-05-01
forum: General Help
---

### Post by candtalan on 2012-05-01
Using Ubuntu 12.04, I have created a desktop executable (I think, using this useful help [http://askubuntu.com/a/128284](http://askubuntu.com/a/128284) )  which will cause a script to run (an rsync activity). I want to  be able to have the activity run in a terminal (so that I can see its progress). I did this fairly easily in Ubuntu 10.04 because there were gui facilities to create a launcher on the desktop and one of the several options included 'run in terminal'.
Now in Ubuntu 12.04 I have my desktop executable containing with the command
/home/user1/bin/myscript-1a.sh
 but this does not seem to invoke a terminal
What command will cause my script to run in a terminal please?
tia


edit:
Found it!  :-)
gnome-terminal -e /home/user1/bin/myscript-1a.sh

---

### Post by Jose Catre-Vandis on 2012-05-01
Either:

If a bash script run it with the -x option and you will see everything in all its glory in a terminal.

Or just run your executable from a terminal

Or

For the rsync part tell your script to open up a new terminal:

```
xfce4-terminal -e rsync ......
```

---

### Post by candtalan on 2012-05-01
> **Jose Catre-Vandis said:**
> Either:

If a bash script run it with the -x option and you will see everything in all its glory in a terminal.

Or just run your executable from a terminal

Or

For the rsync part tell your script to open up a new terminal:

```
xfce4-terminal -e rsync ......
```

thanks!

---

