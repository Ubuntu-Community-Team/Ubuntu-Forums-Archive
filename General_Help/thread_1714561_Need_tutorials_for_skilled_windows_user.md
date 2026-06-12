---
title: "Need tutorials for skilled windows user"
date: 2011-03-25
forum: General Help
---

### Post by swinghein on 2011-03-25
I am a moderately skilled windows user with some dos knowledge that has just transitioned my PCs over to Ubuntu. this is the first time I have had ANY exposure to Unix/Linux. I am looking for some literature or video tutorials that will help me transition to Ubuntu. The basic functions are so similar to windows and mac OS X that I am moving easily around the desktop, but I want to go deeper. I want a little history of how we got from Unix to Ubuntu but quite honestly I don't know what I can do with what I have.

Can someone take me to school please?

---

### Post by Script Warlock on 2011-03-25
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[http://en.wikipedia.org/wiki/Ubuntu_(operating_system](http://en.wikipedia.org/wiki/Ubuntu_(operating_system))

---

### Post by swinghein on 2011-04-17
Thanks, all were helpful!

---

### Post by mrcollinz on 2011-04-17
YouTube is also a very useful tool lots of information and walkthrough's available there.

Good Luck!:)

---

### Post by Spyderkid on 2011-04-17
a couple of basic commands you might want to know (if you don't anyway)...

ls -l  =  displays whats in a directory
cd [folder name] = change a directory
man [command] = shows what a command does and its options
mkdir [name of folder] = make a directory
rm [filename] = remove file
rm -r [folder name] = remove folder and contents

---

### Post by swinghein on 2011-04-17
Thanks for the commands, I just accessed the terminal for the first time yesterday. Slow going, but I'm on my way.

---

### Post by Drenriza on 2011-04-17
Well if your going to use the terminal try the following

Lets say you want to use a command for dns but you cant remember the command.
```
apropos dns
```
will give commands related to dns.
or ```
apropos wifi
```
gives commands related to wifi and so on.

Try read 
```
man hier 7
```
what els that is helpfull is
```
[command] --help
``` gives options to a command
```
which [command] shows the location of the file for executing & using the command
```

If you want to know something else.
permissions, paths, folder placement, or something else. Let me know

---

### Post by mrcollinz on 2011-04-17
LOL@windows exists solely to give linux users something to laugh at..

Kudos to you sir

---

### Post by coldraven on 2011-04-17
Press Ctrl+Alt+T to get a terminal.
Also ```
man -k your-word-of-interest
``` will find all the man pages that mention your-word-of-interest.

---

### Post by Spyderkid on 2011-04-19
Thanks :)

[COLOR="Blue"]And also if your looking for bash scripting (the defualt linux script) then ill give you a quick run through... (if you don't know how to anyway)


to start off you need a text editor (gedit)
open it up.


then you need to tell the computer that its a bash script so type *#!/bin/bash* on the top line.
[/COLOR]
[B]_VERY IMPORTANT_
you need to find the script you've made and right click on it and go to properties > permissions > and check the box that says "allow executing file as a program" if you don't then the script will not run if you open it.
(alternitavly you can use the command like and use *chmod [FILENAME] * to change the permissions so its a program not a text file.) [/B]


[COLOR="SeaGreen"]then you can start beginning your script...

to start we can just make a script that just has a reply (an echo)

```

echo "hello, this is my first script"
sleep 1

```
(the sleep one pauses the script for a second so that you can read what it says.


now you might want to know about variables a key part of a interactive script...?

to use a variable is not too complicated, heres how...

```

echo "what day is it today?"
read DAY
echo it is $DAY today
sleep 1

```

if you run it in a terminal you should see this...

```

what day is it today?
Tuesday (you type this line in reply to the question)
it is Tuesday today

```
[/COLOR]
[COLOR="DarkOrange"]okay now to explain...

it asks you a question using echo (not too hard to grasp that) then you write a reply... the command **[B]read**[/B] does just that and reads what it is you wrote and turns it into a variable.
You can use this variable by adding an _**$**_ then the name of which you defined earlier, in this case DAY. so you get _**$DAY**_ this means that your script will replace _**$DAY**_ with the words you typed in earlier in this case tuesday.

sleep 1 does the same as before, to stop the script ending before you have finished reading.[/COLOR]



[COLOR="Purple"]thats a quick tutorial for very basic bash scripts for you :D[/COLOR]

---

