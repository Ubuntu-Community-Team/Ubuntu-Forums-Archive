---
title: "My Ubuntu learning project!"
date: 2011-07-01
forum: General Help
---

### Post by Henkos on 2011-07-01
Hello Linux folks!

My name is Henrik and I live in Sweden, I was recently introduced to Ubuntu by a friend and it really got me excited. As I understood the OS should be better in almost all possible ways than Windows. So what I have done is that I have dual booted ubuntu along side with Windows 7 that was my first OS. This project's goal is to master Ubuntu with my very own hands and have good knownledge of the programming language Lua, I should also be able to understand simple PHP/CSS/C++. But for a start I will only focus on learning Lua and Ubuntu.

Why I created a thread in this section is becuse I would like to get help with whatever I'm currently learning, for example I will start off by installing several programs that I do like to have on the computer. Once I have done the basics I will try to host an Open-Tibia server, it's an open source so if you would be interested in what it is just google it.

**First Achievements:**

[LIST]
[*] Be able to install any program without any problems.[I] (For a start, Spotify, Tibia, Heroes of Newerth, Remere's map editor, Minecraft and Tortoise SVN)
[/I]
[*]Get basic knownledge how the terminal works and get to know a few commands.
[*]Customize my interface, I want to feel comfortable with Ubuntu.
[*]Be able to write basic Lua.
[*]Update to the latest ubuntu version, I don't know what version I'm currently running.
[/LIST]
These are my first goals to achieve, I will post all the progress I do in posts below. As the thread is located in the general help section I would love if you guys could write small 'how to' posts that possibly could help me out with my goals, I would appreciate it.

[I]Yours,
Henkos.
[/I]

---

### Post by Henkos on 2011-07-01
Feel free to help me out with any of these steps, I'm going to bed now and I would love to wake looking at some sweet posts! :D

**What I have learned so far regarding the terminal:**

[LIST]
[*] ps -A [I]This command will show what processes the computer currently are running.
[/I]
[*] ls [I]This command will show what paths that are available or what documents/files that's in the current directory.
[/I]
[*] kill 9- id *This command will kill the selected process.*
[/LIST]

---

### Post by Henkos on 2011-07-02
Could anyone tell me how to install a basic program? I'm having a hard time trying to install any program...:(

EDIT: Could anyone also tell me how to upgrade my ubuntu software to the newest release?

---

### Post by Matt__ on 2011-07-02
you can install software in several ways.

1. administration/software manager and browse/search
2. download a .deb package click on it to install
3 administration/synaptic package manager and browse/search
4 open a terminal (in accessories) and use the command; sudo apt-get install <name of software package>

for upgrading go to administration/update manager or open a terminal and use the follow command;
```
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get clean && sudo apt-get autoremove
```(you can select this command then middle  mouse click to paste it into the terminal)

the && lets your system go to the next command in the line, but only if the previous one completed first.

update grabs a list of possible updates from the server

upgrade applies those listed updates and the -y automatically says yes to the accept dialog that will appear

clean and autoremove clean up the download cache and uneeded package elements

//edit: to find your ubuntu version type this into a terminal. ```
lsb_release -a
```

---

### Post by Mark Phelps on 2011-07-02
Speaking from experience, one of the easiest ways to become disenchanted with something new is to set your expectations too high.  For example, your first goal of being able to install ANY program without ANY problems -- is simply NOT achievable.  Period.

As already indicated, the ways to install apps range from very simple to very hard.  When you progress to the very hard area (compiling from source, building objects, and coverting them into runtime executables), you ARE going to encounter problems.

In nearly ALL cases, this is due to either (1) unmet dependencies (meaning, you need a dev version of a library installed), or worse, (2) unsatisfiable dependencies (meaning, you have something on your PC that conflicts with something else you need to install).

SOME aspects of using Ubuntu have been made simpler over the years; others, like installing from source, are always going to be HARD.  Don't set yourself up for failure by expecting to be able to install ANY program without ANY problems.  Be realistic.

---

### Post by Henkos on 2011-07-03
> **Matt__ said:**
> you can install software in several ways.

1. administration/software manager and browse/search
2. download a .deb package click on it to install
3 administration/synaptic package manager and browse/search
4 open a terminal (in accessories) and use the command; sudo apt-get install <name of software package>

for upgrading go to administration/update manager or open a terminal and use the follow command;
```
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get clean && sudo apt-get autoremove
```(you can select this command then middle  mouse click to paste it into the terminal)

the && lets your system go to the next command in the line, but only if the previous one completed first.

update grabs a list of possible updates from the server

upgrade applies those listed updates and the -y automatically says yes to the accept dialog that will appear

clean and autoremove clean up the download cache and uneeded package elements

//edit: to find your ubuntu version type this into a terminal. ```
lsb_release -a
```

Thanks! I will try this later. :)

> **Mark Phelps said:**
> Speaking from experience, one of the easiest ways to become disenchanted with something new is to set your expectations too high.  For example, your first goal of being able to install ANY program without ANY problems -- is simply NOT achievable.  Period.

As already indicated, the ways to install apps range from very simple to very hard.  When you progress to the very hard area (compiling from source, building objects, and coverting them into runtime executables), you ARE going to encounter problems.

In nearly ALL cases, this is due to either (1) unmet dependencies (meaning, you need a dev version of a library installed), or worse, (2) unsatisfiable dependencies (meaning, you have something on your PC that conflicts with something else you need to install).

SOME aspects of using Ubuntu have been made simpler over the years; others, like installing from source, are always going to be HARD.  Don't set yourself up for failure by expecting to be able to install ANY program without ANY problems.  Be realistic.

What you are saying is absolutely right, but I don't like to run ubuntu over windows when I can't even run my favorioute programs, and that's why I give up after some hours everytime. Later on I think; this can't be to hard? And I start ubuntu again and realise that I can't do it.

---

