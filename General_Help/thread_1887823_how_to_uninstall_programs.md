---
title: "how to uninstall programs?"
date: 2011-11-28
forum: General Help
---

### Post by Matrix01 on 2011-11-28
how do u uninstall programs on Xubuntu?

---

### Post by beesthorpe on 2011-11-28
well I go to the software centre search for name of the application, select it and click the "uninstall" button.  You could also do much the same in Synaptic, or if that's just too easy use apt-get in the terminal :)

---

### Post by Matrix01 on 2011-11-28
[ATTACH]208117[/ATTACH]
i clicked remove,
that did not work.


> **beesthorpe said:**
> well I go to the software centre search for name of the application, select it and click the "uninstall" button.  You could also do much the same in Synaptic, or if that's just too easy use apt-get in the terminal :)

---

### Post by claracc on 2011-11-28
In xterm, through command line:

sudo apt-get purge name_of_the program (in order to uninstall the program and the configuration files)

then sudo apt-get autoremove to delete dependencies

---

### Post by Matrix01 on 2011-11-28
[ATTACH]208121[/ATTACH]

unable to type passward on terminal.

> **claracc said:**
> In xterm, through command line:

sudo apt-get purge name_of_the program (in order to uninstall the program and the configuration files)

then sudo apt-get autoremove to delete dependencies

---

### Post by zaiger on 2011-11-28
> **Matrix01 said:**
> [ATTACH]208121[/ATTACH]

unable to type passward on terminal.
The password doesn't actually show up visually in the terminal. Just type it out and press enter.

---

### Post by Matrix01 on 2011-11-28
typed my passward,
and this' output.
[ATTACH]208124[/ATTACH]

and this' program i tried to uninstall
[ATTACH]208125[/ATTACH]


> **zaiger said:**
> The password doesn't actually show up visually in the terminal. Just type it out and press enter.

---

### Post by Elfy on 2011-11-28
When you are pasting commands in - only paste the command not anything else.

sudo apt-get purge xfburn

---

### Post by lisati on 2011-11-28
Put one command per line, and be careful to copy just the command and not the explanation! :D

---

### Post by Elfy on 2011-11-28
> **lisati said:**
> Put one command per line, and be careful to copy just the command and not the explanation! :D

Almost uninstalled sudo as well :(

---

### Post by claracc on 2011-11-28
You have to introduce a command on each line:

sudo apt-get purge xfburn 

and then press enter, once uninstalled xfburn, you write the command:

sudo apt-get autoremove

---

### Post by Matrix01 on 2011-11-28
thank u.
[ATTACH]208128[/ATTACH]


> **claracc said:**
> You have to introduce a command on each line:

sudo apt-get purge xfburn 

and then press enter, once uninstalled xfburn, you write the command:

sudo apt-get autoremove

---

### Post by claracc on 2011-11-28
You are welcome.

Please, don't paste blindly commands in xterm because you can cause a mess. 

To know what commands mean and do you can write in a xterm:

man name_of_the_command


Also, you can read some important ubuntu documentation:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

If your problem has been solved, please, mark the thread as solved in order other people can find solutions easily

---

### Post by enjoijesus94 on 2011-11-28
ok lets say i have installed cheese
now i wont it gone so i type in termianl

sudo apt-get autoremove cheese

just use autoremove command:popcorn:

---

