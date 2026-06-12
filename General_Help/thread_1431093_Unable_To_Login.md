---
title: "Unable To Login"
date: 2010-03-16
forum: General Help
---

### Post by BalaViknesh on 2010-03-16
Unable to Login to Ubuntu 9.10.

I didnt do anything strange to cause this kind of error. still now I had kept my Desktop in Auto Login so there was no issues.

all Of a sudden when i rebooted my machine, it was asking my root password and even when i enter that it was not allowing me to login. 

Can anyone plz help this. this is really a matter of urgency.

---

### Post by lorsen on 2010-03-16
Does it ask for the root password at the login screen or at the console?
Does it say something about an error or an installation?

---

### Post by BalaViknesh on 2010-03-16
> **lorsen said:**
> Does it ask for the root password at the login screen or at the console?
Does it say something about an error or an installation?

It asks 4 pwd @ Login Screen and even if i enter it takes me back to the same page.

---

### Post by BalaViknesh on 2010-03-16
any suggestions on this. 

Am awaiting replies to make my Machine get back......

---

### Post by rnerwein on 2010-03-16
hi
may be a silly question. have you set up a root password ? if not you have to login with your
user account.
ciao

---

### Post by BalaViknesh on 2010-03-17
> **rnerwein said:**
> hi
may be a silly question. have you set up a root password ? if not you have to login with your
user account.
ciao


No. I dont have any Root Password.... When I try to login with my user account it shows a blank screen with some text and loops me back to the login screen page again asking Password.... Weird....

---

### Post by soltanis on 2010-03-17
Are you able to log in to a virtual terminal?

Press Ctrl+Alt+F1, type your credentials. If you see a shell prompt it worked, otherwise it should give you some kind of error message that should help.

---

### Post by BalaViknesh on 2010-03-17
> **soltanis said:**
> Are you able to log in to a virtual terminal?

Press Ctrl+Alt+F1, type your credentials. If you see a shell prompt it worked, otherwise it should give you some kind of error message that should help.

where Should I do Ctrl+Alt+F1.. In the Login Screen or while Booting. Sorry If this sounds Simple.. I dont want to Loose Any data whch I have..

---

### Post by lordskid on 2010-03-17
yes at the login screen

---

### Post by BalaViknesh on 2010-03-18
> **soltanis said:**
> Are you able to log in to a virtual terminal?

Press Ctrl+Alt+F1, type your credentials. If you see a shell prompt it worked, otherwise it should give you some kind of error message that should help.

am able to get into the shell prompt without any errors and tried sudo startx.

Output is:

Fatal Server Error: Cannot establish any listening sockets. 
and it asked me to check in a var log file and there i was able to see

 (WW) xf86CloseConsol : KDSETMODE failed : Bad file descriptor
(WW)xf86closeConsole:VT_GETMODE failed: Bad file descriptor
(WW)xf86OpenConsole: VT_GETSTATE failed: Bad file Descriptor.

Please get me into the GUI.

---

### Post by BalaViknesh on 2010-03-18
This thread doesnt stand still.

Resolution:

Updated the packages of my system after getting into Ctrl+Alt+F1
There are few packages which went missing. Which I added manually and did Startx.... 

Whoooompppp.... Like a Bang it logged in resolving all my probs...

---

