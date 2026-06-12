---
title: "Running an application with root privileges."
date: 2012-02-27
forum: General Help
---

### Post by clipod on 2012-02-27
Hi Everyone,
I am fairly new with linux. I have been using ubuntu for a while.
I am having few java based applications which need to get root privileges to write into logs during running an application. I dont want to login as a root user through my terminal to launch the application or make changes to my user account so that it acts as a root. 

I only want few application that runs as root. Is there any alternative where I can put in .sh executable to run as root before launching an application. I can store my root password in that .sh file if I need to. I am new to shell scripting so can someone let me know a step by step procedure for that.

---

### Post by forrestcupp on 2012-02-27
You could just create a launcher, and in the command line just put **gksudo** with the command and/or path to the executable file. Or you could create a script with as many commands as you want, but use gksudo to launch whatever you want to run.
```
#! /bin/bash
gksudo *command /path/to/file*
```I don't think you'll be able to get it to automatically enter passwords, though.

---

