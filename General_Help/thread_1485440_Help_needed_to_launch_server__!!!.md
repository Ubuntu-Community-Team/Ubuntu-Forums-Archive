---
title: "Help needed to launch server  !!!"
date: 2010-05-16
forum: General Help
---

### Post by jee_bee on 2010-05-16
im new into lubuntu add there is no option that i can find
to launch the script that launch my gaming server in a terminal
without typing the command into the terminal manualy

my script:

> cd /srcds
./srcds_run -console -game cstrike +map de_dust2 -maxplayers 24 -tickrate 100


there is no create launcher option in lubuntu

my script work like a charm .. but it launch as a prossess and im not able to acces it ( the terminal wiht the active server)


how can i start my server script in a terminal normaly   ??
or any other way to ave a shortcut on my desktop to launch my server.....    THX!!!!

---

### Post by Ocxic on 2010-05-16
cd /srcds
./srcds_run -console -game cstrike +map de_dust2 -maxplayers 24  -tickrate 100 &

the "&" will send the proccess to the background giving you access to the terminal (you may have to press enter to see the prompt)

---

### Post by jee_bee on 2010-05-16
nope it stil go in process i want to open it in a terminal and keep the terminal open not send it in background !

---

### Post by jerome1232 on 2010-05-16
What terminal emulator does lubuntu use?

I know with gnome-terminal you can make a launcher like this

```
gnome-terminal -x put-command-here
```

That would launch gnome-terminal and execute whatever you type after -x, I'm sure your terminal emulator has similiar options, check out it's man page.

---

### Post by jee_bee on 2010-05-17
bhaaa im lostttt !!!

> exec lxterminal
./srcds_run -console -game cstrike +map de_dust2 -maxplayer 24 -tickrate 100

will pop the lxterminal on but with no command in!
  
it cannot be that hard !!! i just want a shortcut on my desktop to launch...
> /srcds_run -console -game cstrike +map de_dust2 -maxplayer 24 -tickrate 100  

in the > /srcds folder

THX !!!!

---

### Post by jerome1232 on 2010-05-17
From the man page of lxterminal

```
       lxterminal is a program that provides a terminal emulator for the
       desktop, usually for LXDE. It is a lightweight GTK+ 2.x based desktop
       panel.

OPTIONS
       This program follows the usual GNU command line syntax, with long
       options starting with two dashes (`-´). A summary of options is
       included below.

       -e STRING --command=STRING
           Execute the argument to this option inside the terminal.

       -t STRING --title=STRING
           Set the terminal´s title.

       --working-directory=DIRECTORY
           Set the terminal´s working directory.

```

There is alot more but that covers what we want.

You should be able to make a script that does what you want like this

```
#!/bin/bash
lxterminal --working-directory=/srcd -e ./srcds_run -console -game cstrike +map de_dust2 -maxplayers 24 -tickrate 100
```

---

### Post by jee_bee on 2010-05-18
dude still nothing it simpli do nothing when i click on it 
the situation is realy anoying i just want a shortcut to start
my server on my desktop........

let get back to the basic...

LUBUNTU 10.04

THERE IS NO WAY TO CREATE A LAUNCHER
(i remember launching a script from a launcher not by clicking on it)

my  file is      " ***.sh "   and in the proprities its tik as executable

i dont know what im missing...

---

### Post by jee_bee on 2010-05-18
ho and by the way to prove you than im not ... your script alone aint never gona work because a "s" in missing.....


#!/bin/bash
lxterminal --working-directory=/srcd[COLOR="Red"]s[/COLOR] -e ./srcds_run -console -game cstrike +map de_dust2 -maxplayers 24 -tickrate 100

---

### Post by jerome1232 on 2010-05-18
Ah I must of missed that when copy and pasting it.

So is that working for you?

---

### Post by jee_bee on 2010-05-18
nope its not launching anything... no terminal..  (no lxterminal if u prefer)

 :???:

---

### Post by jerome1232 on 2010-05-18
Did you make the script executable? Far as I can tell that *should* work, no way to test it though.

---

### Post by jee_bee on 2010-05-18
i did it ... i mention it in previous post......

---

### Post by jee_bee on 2010-05-18
u mean by go in the proprities and tic the executable option... yes

---

### Post by jerome1232 on 2010-05-18
Just tested lxterminal with a few commands and revised it a bit

```
#!/bin/bash
lxterminal --working-directory=/srcds -e "./srcds_run -console -game cstrike +map de_dust2 -maxplayers 24 -tickrate 100"
```

And I mean this launcher script that I'm trying to help you create, not the game server executable.

edit:forget that s again :)

---

### Post by jee_bee on 2010-05-18
i bet u problem came from something missing on that all empty 
(wish is good) distro #lubuntu# i hope u understand each other (lol) but like i say in ubuntu i create the script MY SELF
BUT in ubuntu i create a launcher TO start my script ...
in Lubuntu U CANNOT CREATE LAUNCHER

---

### Post by jee_bee on 2010-05-18
i will test it in 5 minutes....

---

### Post by jee_bee on 2010-05-18
still not working.... how did im supose to launch my script
im tring to dbl-clic and right clic it and click terminal in shell menu.... just to let you know how i try to launch it..


THX!!!

---

### Post by jee_bee on 2010-05-18
hey the script is not the problem i instal a teamspeak .. it came whit the starter .sh and it also not start the server..

---

### Post by jee_bee on 2010-05-18
so my bet will be.... lxterminal doesent want to click open a script    
i ave to do...    


> cd /srvt
./myscriptname.sh

how ca i ave an execution shortcut for those script ?????

I WANT A SOLUTION TO LAUNCH MY "*.sh" file without aving to enter a terminal command

---

### Post by jee_bee on 2010-05-18
in ubuntu i will simply create a launcher  to my "*.sh" file





CANNOT CREATE LAUNCHER IN LUBUNTU

---

### Post by jerome1232 on 2010-05-18
Yes I understand that, you have explained it many times. There is no need for caps.

 I was trying to help you create a launcher script that you could place on your desktop to use, however as that is not working I started googling information about lxde and how to create launchers.

I found that there is a program called lxshortcut that can generate .desktop files (launchers) which you can then edit, then place on your desktop or drag to a panel and use.

So maybe try installing lxshortcut
```
sudo apt-get install lxshortcut
```

Use it to generate a .desktop file
```
lxshortcut -o ~/Desktop/cstrike.desktop
```

On my machine it pop's up a gui that allows me to configure the launcher as if I had used the regular right click method in gnome.

Enter the details and put the .desktop file on your desktop if it's not already there, or drag it to your panel.

I hope that helps you out.

edit: I got my information from [here]("http://forum.lxde.org/viewtopic.php?f=4&t=445") and [here]("http://forum.lxde.org/viewtopic.php?f=3&t=182&p=1647&hilit=lxshortcut#p1647")

---

### Post by jee_bee on 2010-05-18
the gui is oppening......
its creating a file on desktop... not usable i tic the executable option  i set it to start in terminal... no luck...

---

### Post by jee_bee on 2010-05-18
the problem realy come from the lxterminal it self
it doesne want to exec the script   if im not aleady the terminal
and typing the command manualy

---

