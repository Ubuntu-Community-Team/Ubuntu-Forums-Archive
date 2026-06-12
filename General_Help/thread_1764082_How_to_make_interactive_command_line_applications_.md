---
title: "How to make interactive command line applications more friendly (bash feature) ?"
date: 2011-05-21
forum: General Help
---

### Post by frogo on 2011-05-21
Hi, 

I'm using a java application that runs as an interactive command line (in a terminal). My problem is that it's rather unfriendly as an interaction mode as it's minimalistic (bournish, for all i understand): it doesn't allow going to and fro with arrows, there's no history and so on. So I have to type all commands every time and have to retype it if I missed something at the beginning of the line, or I have to copy and paste from a txt editor. 

The strange thing is that I have seen the same application running on a Windows box and allowing for all the sugar. So I'm not sure if it's because of the shell script I run (as opposed to the .bat) or whether it has to do with system or profile settings in my shell. 

For information, the shell script starts with:
```
#!bin/sh
```I've replaced it with:
```
#!bin/bash
```in hope I would have something closer to my normal terminal. The app runs but it doesn't change anything to the interactive mode. 

I'm rather clueless regarding sh/bash and so on. I've seen the manuals but I'm not entirely at home understanding and using their options. I know that there's a .bashrc and perhaps something like a profile somewhere, but I don't really know how to do things with these without risking messing up . At bottom, I'm not sure even whether there's something I can do---I have only hopes... 

Any suggestion or pointer most welcome. 

Many thanks

---

### Post by dwhitney67 on 2011-05-21
You are not making yourself very clear.  You indicated that you are running a Java program (that collects user input), yet you are referring to Bash.  What does Bash have to do with the Java program?

If you want to support advanced features such as in-line editing, history, arrow key functionality, etc with your Java application, then you need to perform some more research into the topic wrt to how Java collects input.  Whether you launch this application using Bash, Dash (sh under Ubuntu), or whatever won't make a difference.

---

### Post by frogo on 2011-05-21
> **dwhitney67 said:**
> You are not making yourself very clear.  You indicated that you are running a Java program (that collects user input), yet you are referring to Bash.  What does Bash have to do with the Java program?

If you want to support advanced features such as in-line editing, history, arrow key functionality, etc with your Java application, then you need to perform some more research into the topic wrt to how Java collects input.  Whether you launch this application using Bash, Dash (sh under Ubuntu), or whatever won't make a difference.

ah yes, I wasn't very clear, sorry (also, I'm not a native speaker)

So the main points are: 
- I'm not developing that application, I'm only using it. 
- I don't know Java
- I know next to nothing regarding bash
- The application is run in a terminal and started by invoking a shell script. The application is some sort of REPL (it stays in the terminal and its interactive---a more insightful description is beyond me).

My problem is that I don't have bash features (move on the line and history, in particular) when running that application. 

I can only assume that to make these features appear depends on one of the following:
1- the script invoking the application
2- the way of invoking the script 
3- the application itself (Java, then)

Since I  have seen the application running on Windows with bash features, and the only difference was in the script that starts the application, I thought that the application was not responsible for the absence or presence of bash features. So I assumed what matters is 1 or 2.

The app comes with a sh script. I changed that script to be a bash one (1) and I invoke it as a bash script (2). However, that still doesn't give bash features when running the applications.   

So, my question is about bash and whether there's a way of turning on/off features; whether there are options for this, to place, for example, in the script or to use when invoking it. Or whether that's controlled in some environment or profile on Ubuntu. Or whether, again, something else is the case... 

Hope this makes more sense. This is probably a very basic question about bash, but I thought it made more sense to ask it here given the chance that programmers may have seen that before. I could ask that the thread be moved to Absolute Beginners if it's more appropriate. 

Many thanks

---

### Post by cgroza on 2011-05-21
In python, the functionality is provided by importing the module "readlines". 
I am not sure there is something you can do. If the application is coded not to take advantage of them, it never will.
The only option I see is contacting it's developer.

---

### Post by Telengard C64 on 2011-05-21
> **frogo said:**
> ```
#!bin/bash
```

Shouldn't that be **#!/bin/bash**?
:confused:


Probably wouldn't help your situation anyway. You seem to be fighting against whatever Java methods are used to gather input from the terminal.

---

### Post by jamesjenner on 2011-05-21
Java has primitive Text based interface tools out of the box. You won't be able to get this functionality your requesting without changes to the Java program your using (if at all possible, the way to do this would be far to much work for the benefit gained IMHO). 

Sorry mate, but it's going to be a no go.

---

### Post by frogo on 2011-05-22
@Telengard: yep, that was a typing mistake in my message. 

@+James: I still don't think it's java related, but OS, or rather bash, related.


As a follow up... 

I added the following line to my [FONT=Courier New].bashrc[/FONT]: 
```
stty -echoctl
``` See: [http://www.computerhope.com/unix/ustty.htm](http://www.computerhope.com/unix/ustty.htm). 

It allows using the left and right arrows, to move around and modify what I'm typing in the terminal when running the application. Before, pressing arrows echoed things like: ^[[D and ^[[C instead. 

It's not really a solution, however. The up and down arrows are just that (up and down on the screen of the command line). So, I don't get a mapping between up and down and backward/forward Bash history.   Worse, 'DELETE' doesn't do anything until I press another key and then it echoes a control sequence.

I stumbled on stty by chance and I don't really understand it. I'm not convinced that's the best way to enable (rather than approximate) bash  features. Nevertheless, that heightens the hope of finding a bash-like interaction when running the app by tweaking the bash configuration. 

So suggestions on how to tweak bashrc, or any bash related file, are still most welcome.

Thanks

---

### Post by frogo on 2011-05-29
bumping, I'm not less confused 

I still don't know whether I'm being silly in trying to set bash features for a terminal running a java app.

I've tried tweaking .inputrc (defining keypad mappings) or even .bashrc but to no great or useful effect. 

If it seems possible to influence the shell with general settings, I can't find the right ones or the right way to enforce them.

---

### Post by Smart Viking on 2011-05-29
Bash = [http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29)

You are not running the Java program "in" bash, you are executing the Java program "from" bash, the Java program does what ever it wants to do. If you want to change the way the program behaves, you will have to change the source code, which requires programming experience to succeed.

---

### Post by frogo on 2011-06-02
> **Smart Viking said:**
> Bash = [http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29)

You are not running the Java program "in" bash, you are executing the Java program "from" bash, the Java program does what ever it wants to do. If you want to change the way the program behaves, you will have to change the source code, which requires programming experience to succeed.


ok, I think I'm coming to term with the fact there's nothing I can do about it. I'll mark that as solved. 

many thanks for your time

---

