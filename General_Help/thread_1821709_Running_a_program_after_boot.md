---
title: "Running a program after boot"
date: 2011-08-09
forum: General Help
---

### Post by Rawful on 2011-08-09
I am using a small ubuntu command-line only distro (Ubuntu Mini Remix) to run off of a LiveCD or USB stick. I need it to run a program as root as soon as it is finished booting, automatically. I cannot for the life of me figure out how to make it run my program. 

I have tried putting a script into rc2.d (when I type runlevel at the command line, it tells me it is level 2) that simply contained:

```
#!/bin/bash

qct

```(qct is the name of my program)


I did the chmod u+x on the script. It does not run my program, though. I have no idea if it was a naming issue or not. I do not understand the naming scheme.

When it boots, and doesn't run my program, I can type sudo qct at the command prompt and it runs fine.

What am I missing? Someone help me out please.

---

### Post by dandnsmith on 2011-08-09
First thing is to ensure that qct is within the path seen at boot time - easiest way is to give the full path to the executable, not just the name without path.

---

### Post by Rawful on 2011-08-09
Alright, I have typed out the full path (/bin/qct) in the script to no effect.

---

