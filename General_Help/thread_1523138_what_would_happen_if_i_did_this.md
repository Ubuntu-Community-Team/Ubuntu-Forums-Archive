---
title: "what would happen if i did this?"
date: 2010-07-03
forum: General Help
---

### Post by unter on 2010-07-03
if i log in for su in root directory and type

```
 chmod -R 7777 *
```

---

### Post by robsoles on 2010-07-03
Definitely an insecure system and, AFAIK, certain parts of the system will refuse to play along anymore because they have very very bad file permissions!

You could always try it in a VM you don't care about - want me to? (I can make a backup copy of VM's HDD and then trash it this way and report back in about half an hour of request to be that silly ;))

---

### Post by unter on 2010-07-03
try it if you like! :D i shall like to hear

i will do myself just as soon as ive finished wrecking the current ubuntu in my virtual box by making copies of an image in an infinite loop .... :popcorn:

---

### Post by CharlesA on 2010-07-03
You run that command as root in / and you will have an upbootable system.

---

### Post by unter on 2010-07-03
> **CharlesA said:**
> You run that command as root in / and you will have an upbootable system.


for chmodding which particular files will this happen?

---

### Post by CharlesA on 2010-07-03
I'm not sure which particular files causes it, but I know that most of the files off / need specific permissions set.

---

### Post by robsoles on 2010-07-03
> **unter said:**
> for chmodding which particular files will this happen?

many many files that belong to root have very specific permissions and various parts of your system, primarily but not solely selinux, will just bomb (quite purposefully on part of Authors in most cases) if they have bad permissions.

It's just silly and really, thinking about it, your purpose cannot be good: What are you trying to do there?

---

### Post by unter on 2010-07-03
> **robsoles said:**
> many many files that belong to root have very specific permissions and various parts of your system, primarily but not solely selinux, will just bomb (quite purposefully on part of Authors in most cases) if they have bad permissions.

It's just silly and really, thinking about it, your purpose cannot be good: What are you trying to do there?

nothing its very curiosity :D

i can hardly program hello world and if i wanted to  "hacker" i would try for something more interesting than wrecked computer :D

---

### Post by unter on 2010-07-03
yes. system will not boot after full privlidges to entire ubuntu. i confirm this. :)

---

### Post by surfer on 2010-07-03
happened to me once. in a bash script i misspelled the directory i wanted to [FONT="Courier New"]chmod[/FONT] to 7777; unfortunately i wrote a slash in front of the undefined variable...
i don't remember if the system still boots (but i don't see why it shouldn't), but the system is screwed beyond repair... probably even worse than [damn vulnerable linux]("http://www.damnvulnerablelinux.org/").

---

### Post by robsoles on 2010-07-03
> **surfer said:**
> happened to me once. in a bash script i misspelled the directory i wanted to [FONT=Courier New]chmod[/FONT] to 7777; unfortunately i wrote a slash in front of the undefined variable...
i don't remember if the system still boots (but i don't see why it shouldn't), but the system is screwed beyond repair... probably even worse than [damn vulnerable linux]("http://www.damnvulnerablelinux.org/").

refer to unter's post - though I am not sure why you think '... but the system is screwed beyond repair...' doesn't fairly well rule out being able to reboot, though in an older and truly outdated release of some or other distro perhaps it would have though I wouldn't like to be challenged to bet on it!

> **unter said:**
> yes. system will not boot after full privlidges to  entire ubuntu. i confirm this. :)

Thanks unter - may as well mark your crazy thread here as solved pal!

---

### Post by unter on 2010-07-03
is 'damn vulnerable linux' a joke or is it real?

---

### Post by unter on 2010-07-03
> **robsoles said:**
> refer to unter's post - though I am not sure why you think '... but the system is screwed beyond repair...' doesn't fairly well rule out being able to reboot, though in an older and truly outdated release of some or other distro perhaps it would have though I wouldn't like to be challenged to bet on it!



Thanks unter - may as well mark your crazy thread here as solved pal!


:D

i try to mark solved but i think feature not available. *added to title.

---

### Post by Vaphell on 2010-07-03
> is 'damn vulnerable linux' a joke or is it real?

it's real and it's specifically designed to be a security nightmare for educational purposes.

---

### Post by robsoles on 2010-07-03
In top of page containing thread look for 'thread tools' (in red) and click it - look for word solved, last item I think, and click that!

---

### Post by unter on 2010-07-03
> **robsoles said:**
> In top of page containing thread look for 'thread tools' (in red) and click it - look for word solved, last item I think, and click that!


thanks robsoles :P this thread would be nothing without you ...  :D

---

### Post by robsoles on 2010-07-03
That's very kind unter but I reckon just one person who posted had have held back and the thread would be that much less valuable!

do until all thanked;
   thanks poster;
loop;

---

### Post by surfer on 2010-07-05
> **robsoles said:**
>  though I am not sure why you think '... but the system is screwed beyond repair...'


i just meant to say that the system practically can't be fixed after that. a clean reinstall is probably easier than fixing the thing. (you would have to make a list of paths and permissions and chmod everything back).

---

### Post by effenberg0x0 on 2010-07-30
I have installed a new HDD in my Ubuntu 10.04 desktop. This machine acts as a NAS, media, file, web and print-server at my home office. I created a public user and a public group to operate the /media/newhdd/public directory temporarily. 

Yesterday I was very sleepy and did exactly what was originally proposed in this thread, except that the command line also changed user/group of all files (-R) in the pipe to public/public. 

I commited **one** single **stupid** mistake: I was inside /media/hdd and applied the command to **/*** (all file system) instead of ***/** (/media/newhdd/public /media/newhdd/public2 etc). Really, **REALLY** lame. I'm an **idiot**.

Results? Unusable system. Too much work/time to fix everything. Tried, but gave up after hours of hitting my head against the wall. It would take weeks for me to really detect and fix problems.

_Notes to self:_

**1.**I will never sudo again in my life without thinking twice or more. Stop sudoing all the time man...what's wrong with me? 
**2.**I will never use sudo with wildcards again. Gotta stop using wildcards all the time and take the time to use full paths.
**2.**I will never do significant changes to important machines again with no proper sleep and rest.

Reinstalling OS now. Deeply regret not having converted the stable system to a VM... Oh well, nothing I can do now...

Regards,
Effenberg

---

