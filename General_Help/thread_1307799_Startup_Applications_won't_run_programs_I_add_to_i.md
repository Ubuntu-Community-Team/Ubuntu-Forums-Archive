---
title: "Startup Applications won't run programs I add to it"
date: 2009-10-31
forum: General Help
---

### Post by daldude on 2009-10-31
I'm running Ubuntu 9.10 and I added a program to Startup Applications but Ubuntu won't load the program I added to Startup Application at boot up time. If I type the name of the program in the Run Application ((Allt F-2) it shows the program and will run it if I hit enter or click Run so I know Ubuntu is seeing it and I checked for Typos in Star up Applications to make sure I did not spell it wrong.:(

---

### Post by lswb on 2009-10-31
Are you trying to get a program to run before anyone logs in to a desktop? The Startup Applications setting you refer to is for running applications for an individual user after logging in. 

What program are you trying to run?

---

### Post by daldude on 2009-10-31
> **lswb said:**
> Are you trying to get a program to run before anyone logs in to a desktop? The Startup Applications setting you refer to is for running applications for an individual user after logging in. 

What program are you trying to run?

I'm trying to get a program to load after I log in.

The Program is called MINBAR, it's a program for Islamic Prayer Times that will play the call to prayer for each of the 5 daily prayers Muslims preform.

---

### Post by lswb on 2009-10-31
Sometimes certain programs cannot run properly if the desktop is not fully functional when they start up. If you check the command line for some of the existing startup applications, you will see several that include a "sleep 30" or similar statement. You could try running your program with a similar command line.

---

### Post by daldude on 2009-10-31
> **lswb said:**
> Sometimes certain programs cannot run properly if the desktop is not fully functional when they start up. If you check the command line for some of the existing startup applications, you will see several that include a "sleep 30" or similar statement. You could try running your program with a similar command line.

That worked 


Thanks.

---

### Post by lswb on 2009-10-31
afwan!

---

### Post by creatio on 2010-02-20
I'm having the same  problem

I try to run firestarter on startup but it just wont run, first it says the lack of privilege so I add "sudo" in front of the line.

I've tried it on 9.04 and it worked then, bust doesn't seems to be working on 9.10.

help pliss

thanx in advance

---

