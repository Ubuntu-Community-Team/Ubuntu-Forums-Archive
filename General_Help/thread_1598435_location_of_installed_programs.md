---
title: "location of installed programs"
date: 2010-10-16
forum: General Help
---

### Post by ddimit on 2010-10-16
hello recently i have installed a lot of programs and some of them didnt make a shorcut 
i would like to tell me most of the programs we are installing where they are get installed (location) and how can i run them by my self and not by  terminal or by any programs)

---

### Post by Rocket2DMn on 2010-10-16
Many basic programs install to /usr/bin, but if you know the name of the app, you can find it with
```
whereis *appname*
```
then you can create a custom launcher for it on the desktop or on a panel.

Specifically what programs did you install and expect shortcuts for? Most apps have a link under the Applications menu.

---

### Post by cpmman on 2010-10-16
System - Administration - Synaptic Package Manager - right click program - Properties - Installed Files

will list all installed files for that program.

---

### Post by Frogs Hair on 2010-10-16
Start with Preferences > Main Menu and check the boxes for the programs you wish to have on the menu. Some programs run from the terminal , I have a system monitor that does and has to be started by typing the name . You can also press Alt F2 and type the program name into the box and select run.

---

### Post by ddimit on 2010-10-16
edit
last question (a bit general): before 2 weeks i was searching to the net for how to find the commands of each program and one wrote you can find it by typing that(xprop | grep WM_CLASS) my question is if nobody wrote it on the net how should i work to find it? how you people know so many commands? do you read books?

edit
the whereis command is not working with jdownloader
im typing where is jdownloader and not working

---

### Post by WorMzy on 2010-10-16
You must have downloaded jdownloader manually, because I can't see it in the repos. That being the case, I'd suggest looking for a readme file inside the archive you downloaded. It'll probably tell you how to run the application.

As for how we know so many commands: reading helps, there's a lot of great "Linux for Beginners" type books out there. But I think that the best way to learn is to throw yourself into an activity. Try to use Linux as a primary OS, and you'll quickly pick up useful commands and tricks. Ask on the forums if there's a specific task you're trying to do, and people will suggest ways of doing it.

You can learn what a program can do by reading it's man page (assuming it has one), you can do that by opening a terminal and running
```
man <appname>
```

e.g.

```
man apt-get
```

---

### Post by ddimit on 2010-10-18
can you tell me which  books can help me learning useful commands?
some titles etc? thanks

---

### Post by WorMzy on 2010-10-18
I think this would be the best place for you to start: [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

There's some good book recommendations on this page: [http://linuxcommand.org/who_what_where_why.php]("http://linuxcommand.org/who_what_where_why.php"). Some of them are freely available online; others you may be able to read on Google Books.

---

### Post by stephan0h on 2010-10-18
if there is no other way:

in terminal issue command:

which <your program>

(sometimes it may not be clear what's the actual name of the program but you can start typing at the command line and by pressing <tab> all possibilities should be displayed. 

If you don't want to use terminal always you could edit your start-menue manually ...

but generally there should be some magic doing this for you ;-)

---

