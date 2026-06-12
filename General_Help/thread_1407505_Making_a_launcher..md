---
title: "Making a launcher."
date: 2010-02-15
forum: General Help
---

### Post by ron999 on 2010-02-15
Hi
I have a program called 'TubeMaster'.
It works ok with Ubuntu but needs to be run as root.
So I have to use the command:-
```
sudo ./tm++.sh
```
Is it possible to make a launcher for this program so that I can run it from Ubuntu's menu?

---

### Post by akashiraffee on 2010-02-15
Yeah, presuming you are running GNOME you can add things to the menu directly from the menu (it's a point and click GUI). 

I'm not in GNOME right now but if you look around under administration or settings you'll find it.

---

### Post by joeknoodle on 2010-02-15
I'm an amateur, so exercise all cautions. I don't anticpate this information destroying data, but backups never hurt...

Use caution when executing commands or running apps as su, or sudo...

Go to:

System > Preferences > Main Menu

There do:

Select a Category and then click on the box to the right that says "New Item"

Give it a name

Insert the command as you listed, and maybe a comment

You can also click on the "springboard" icon in the upper left to use a custom icon.

Then just select OK and you should see it listed in the Category you chose. On my system this takes just a second or even a minute to show up, but it should work.

---

### Post by mhgsys on 2010-02-15
just right click a panel > add to panel > Custom application launcher > (name it whatever you want to ) command> gksudo ./tm++.sh

---

### Post by ron999 on 2010-02-15
Hi
It's not as simple as that.
I forgot to say, first I have to change directory using command:-
```
cd /home/ron/tm++.linux/TubeMaster++
```
Then I use the sudo./tm++.sh command.

---

### Post by mhgsys on 2010-02-15
then make it; ```
gksudo /home/ron/tm++.linux/TubeMaster++/tm++.sh
```

I guess;

---

### Post by ron999 on 2010-02-15
> **mhgsys said:**
> then make it; ```
gksudo /home/ron/tm++.linux/TubeMaster++/tm++.sh
```

I guess;

No, it won't start up with that command.
```
ron@ubuntu:~$ gksudo /home/ron/tm++.linux/TubeMaster++/tm++.sh
TubeMaster++ detected operating system : Linux
ron@ubuntu:~$
```

But when I change directory then use ./tm++.sh it runs ok, like this:-
```
ron@ubuntu:~$ cd /home/ron/tm++.linux/TubeMaster++
ron@ubuntu:~/tm++.linux/TubeMaster++$ sudo ./tm++.sh
[sudo] password for ron: 
TubeMaster++ detected operating system : Linux
*TubeMaster++ Core Started*
-= TubeMaster++ Started on null =-
-= TubeMaster++ Started on USB bus number 1 =-
-= TubeMaster++ Started on USB bus number 2 =-
-= TubeMaster++ Started on USB bus number 3 =-
-= TubeMaster++ Started on USB bus number 4 =-
-= TubeMaster++ Started on USB bus number 5 =-
-= TubeMaster++ Started on Pseudo-device that captures on all interfaces =-
-= TubeMaster++ Started on null =-
* Conversion Thread Running*

```

---

### Post by mhgsys on 2010-02-15
Erh. 

```
/home/ron/tm++.linux/TubeMaster++/./tm++.sh
```

I'm guessing; I don't have a ./sh file here to test it myself;

anyway; I think you've got my drift,

---

### Post by akashiraffee on 2010-02-15
Write a shell script and use that in the launcher.

```

#!/bin/sh
cd /home/ron/tm++.linux/TubeMaster++
sudo ./tm++.sh

```

---

### Post by ron999 on 2010-02-15
> **akashiraffee said:**
> Write a shell script and use that in the launcher.

```

#!/bin/sh
cd /home/ron/tm++.linux/TubeMaster++
sudo ./tm++.sh

```

That sounds like a good idea.
I will put the script in my usr/bin folder then call up the script from the launcher.
Watch this space...

---

### Post by ron999 on 2010-02-15
I saved the script as 'tubemaster', made it executable and put it in my usr/bin folder.
It runs now if I just use the command **tubemaster**.
But it won't run from the menu, even though in the launcher properties it's pointing to /usr/bin/tubemaster.

---

