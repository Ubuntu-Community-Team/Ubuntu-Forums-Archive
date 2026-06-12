---
title: "Software center issue?"
date: 2012-08-02
forum: General Help
---

### Post by linktopower on 2012-08-02
Hello. Okay I've been messing around with Ubuntu 12.04... But It seems I can not install anything through the Ubuntu Software Center. When I select a program to install, The Install button is like dulled out and I can not press it at all.
even in the file menu I can not install anything.

SO I was wondering is there something I can do to be able to install stuff through the Software center?

---

### Post by lisati on 2012-08-02
Do you have any other software management programs, such as "Synaptic" running?

---

### Post by linktopower on 2012-08-02
Oh yeah I have "Synaptic" But It was not running at the same time as Ubuntu software center.

---

### Post by Dylan1473 on 2012-08-02
Are you running any sort of process related to installing/updating things at all? Anything in the terminal? Did you try logging out or rebooting to make sure any such processes were ended?

---

### Post by ijumpship on 2012-08-02
i have seen this since 11.10, what i know is that if you wait a little it start responding.
i do not know if because my machine are so like me 'OLD', but I am a terminal person so it affects me just a little bit

---

### Post by linktopower on 2012-08-02
> **Dylan1473 said:**
> Are you running any sort of process related to installing/updating things at all? Anything in the terminal? Did you try logging out or rebooting to make sure any such processes were ended?
As far as I know, No. I don't think I'm running anything that  does installing/updating.
> **ijumpship said:**
> i have seen this since 11.10, what i know is that if you wait a little it start responding.
i do not know if because my machine are so like me 'OLD', but I am a terminal person so it affects me just a little bit
I haven' tried waiting I'll give it a try and see what happens.

EDIT: Okay doing what ijumship`said worked kinda. at least the install from the file menu lit up and I was able to install something from Software center.
Still I wonder why the main install button won't lite up?

---

### Post by ijumpship on 2012-08-03
i think there is a bug in the software center and the unity,the worst one you will see is where nothing lights up you click  away just after that a sign comes up'already install reboot'

I think its is that they want us to use nothing but the software center but its buggy. 

Sometimes you cannot find a package after you install it from the software center like Opera.

One thing I learn from linux whatever works for you,keep on doing what you do sammy

---

### Post by Dylan1473 on 2012-08-03
If it's any help and you don't already know, you can also update/install new packages by typing the following in the terminal:

Update:
```
sudo apt-get update
sudo apt-get upgrade
```Search for a package:
```
sudo apt-cache search [KEYWORD]
```Install a package:
```
sudo apt-get install [PACKAGE NAME]
```There's more than that of course but those are the main ones I use. And I generally wouldn't say to just give up and try another method, and I do encourage you to try to get it working, that's just in case you need to update or install things immediately.

---

### Post by linktopower on 2012-08-03
> **Dylan1473 said:**
> If it's any help and you don't already know, you can also update/install new packages by typing the following in the terminal:

Update:
```
sudo apt-get update
sudo apt-get upgrade
```Search for a package:
```
sudo apt-cache search [KEYWORD]
```Install a package:
```
sudo apt-get install [PACKAGE NAME]
```There's more than that of course but those are the main ones I use. And I generally wouldn't say to just give up and try another method, and I do encourage you to try to get it working, that's just in case you need to update or install things immediately.
Yeah I already know about installing things through the Console. its the main way I install most things. 
I've been looking at`software center for awhile now. I'll give a run through the console as a root user and see if its some sort user privileges issue.

But atleast by waiting I can install stuff from software center. but its takes some time for the install thing in the file tab to show up but after that I can click it and it installs.

---

