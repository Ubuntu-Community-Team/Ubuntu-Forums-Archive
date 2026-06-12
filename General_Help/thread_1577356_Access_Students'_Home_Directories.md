---
title: "Access Students' Home Directories"
date: 2010-09-18
forum: General Help
---

### Post by feed5000 on 2010-09-18
I'm using Edubuntu 10.04 in my classroom. I use an administrator account. There are about 8 student accounts on the computer, created as desktop users. I would like to login with my account and be able to view, create, and delete files in the students' home directories. However, I can't figure out how I would give myself this permission.

I've tried sudo chmod, but that won't work, because I'm not the owner of those files.

I've tried sudo chown, but that won't work, because the students need to be owners of their own directories.

So, what is the tactic to use here?

---

### Post by Rasa1111 on 2010-09-18
I am not sure, but interested to learn the answer, 
this could come in handy for the few Ubuntu computers Im about to setup at the Observatory, 
mostly for younger people. 

 good question,..

 and respect to you for getting them to use Ubuntu/Linux. :) <3

---

### Post by Serpher on 2010-09-18
The easiest way to do this is go into your terminal and run the command:

```
gksu nautilus
```


This will open the file as root (Administrator). From there you can browse any directory and change or access any file with ease. There is a more proper way to do this but honestly unless you're not running a whole building of these things this will probably do you fine and save you the headache of configuring user groups and file permissions. On another note terrific job on implementing edubuntu into the classroom. I'm an IT student specializing in Open Source servers and if you need any more help feel free to e-mail or instant message me at [email]mspalmer12@gmail.com[/email] as I would really love for your classroom's Linux experience to be a success.

---

### Post by feed5000 on 2010-10-27
Serpher's recommendation of ```
gksu nautilus
``` does exactly what I need. It has done everything I've need for about a month now. Thank you Serpher.

I am now running almost 25 computers on Ubuntu in our school's CPU lab, with 10 or so users on each. It's gone well so far. I have problems with the graphics crashing altogether on 3 of them, and KTouch is slow in responding to keystrokes on some of the systems, but other than that I've been very pleased with Ubuntu.

---

