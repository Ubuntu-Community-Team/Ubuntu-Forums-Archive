---
title: "Command Line - Tab through alternatives...?"
date: 2010-04-18
forum: General Help
---

### Post by AnotherMuggle on 2010-04-18
I am sure I used to be able to tab through similar results in Ubuntu Terminal.  

For example if I enter:
```
thomas@thomas-laptop:~$ cd D
``` followed by the tab button then I would like to tab through the alternatives..i.e Desktop then Downloads etc.
Instead, nothing happens and I need to press the tab key again which then just echos all the results beginning with D.

I don't seem to be able to do this anymore and wondered if anyone can help out.

---

### Post by colorlessprism on 2010-04-18
with my install i have to enter the first few letters of what i want (ie des).

---

### Post by sisco311 on 2010-04-18
add something like:
```
"\t": menu-complete
```to the ~/.inputrc file.

---

### Post by AnotherMuggle on 2010-04-19
> **sisco311 said:**
> add something like:
```
"\t": menu-complete
```to the ~/.inputrc file.

I may not have explained properly. The auto-completion works, but I'm sure I used to be able to keep pressing the tab key to iterate through the next matches.  Or is that what the command you posted does?

Thanks for the assistance,
Tom

---

### Post by sisco311 on 2010-04-19
> **tomkear2006 said:**
> I may not have explained properly. The auto-completion works, but I'm sure I used to be able to keep pressing the tab key to iterate through the next matches.  Or is that what the command you posted does?

Thanks for the assistance,
Tom

It's not a command, you have to add the line to the ~/.inputrc file & yes, that's what it does. After editing the file you have to start a new bash session (log out or start a new terminal).

---

### Post by AnotherMuggle on 2010-04-19
> **sisco311 said:**
> It's not a command, you have to add the line to the ~/.inputrc file & yes, that's what it does. After editing the file you have to start a new bash session (log out or start a new terminal).

Ah ok. It looks like that file doesn't currently exist at all. Do I just create a new one?

I have that file but it is located in /etc/inputrc  ... same thing?

---

### Post by sisco311 on 2010-04-19
> **tomkear2006 said:**
> Ah ok. It looks like that file doesn't currently exist at all. Do I just create a new one?

yep.

---

### Post by AnotherMuggle on 2010-04-19
> **sisco311 said:**
> yep.

Sorry, do I create the file and enter only the line you posted or does it need to contain other information?

---

### Post by sisco311 on 2010-04-19
> **tomkear2006 said:**
> Sorry, do I create the file and enter only the line you posted or does it need to contain other information?

Just the line I posted.

---

### Post by AnotherMuggle on 2010-04-19
> **sisco311 said:**
> Just the line I posted.

That got it.

Thanks very much :-D

---

