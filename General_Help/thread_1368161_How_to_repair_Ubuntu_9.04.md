---
title: "How to repair Ubuntu 9.04"
date: 2009-12-30
forum: General Help
---

### Post by tempus on 2009-12-30
is there some way to repair an installation of ubuntu 9.04 without destroying the configuration of it? My problem started when trying to upgrade firefox and something stupid that I tried resulting from it. So my question is...can i run a utility that will repair broken files and the like?

---

### Post by oldos2er on 2009-12-30
Without knowing exactly what you did, it's next to impossible to advise you.

---

### Post by tempus on 2009-12-30
> **oldos2er said:**
> Without knowing exactly what you did, it's next to impossible to advise you.

I messed up the installation of Firefox to the point where it will not start when i click on the icon in the applications menu. Rather than reload the entire os from scratch I was hoping to restore that file structure for firefox...if possible.

---

### Post by oldos2er on 2009-12-30
How did you install Firefox?

---

### Post by SchizmWolf on 2009-12-30
Again, it's hard to fix the problem without knowing what changes you made to both Firefox and your OS. 
Have you tried:
```
sudo apt-get remove firefox
```
followed by
```
sudo apt-get install firefox && apt-get update
```
That's a basic procedure, and unless you really borked your system trying to install in the first time, I don't see why it wouldn't work...

---

### Post by tempus on 2009-12-30
> **SchizmWolf said:**
> Again, it's hard to fix the problem without knowing what changes you made to both Firefox and your OS. 
Have you tried:
```
sudo apt-get remove firefox
```
followed by
```
sudo apt-get install firefox && apt-get update
```
That's a basic procedure, and unless you really borked your system trying to install in the first time, I don't see why it wouldn't work...

I borked the system beyond repair...maybe a reinstall will work. :confused:

---

### Post by 3L33T on 2009-12-30
> **tempus said:**
> I borked the system beyond repair...maybe a reinstall will work. :confused:

You are not telling the WHOLE SCENARIO.  If you claim "you borked up the system installing firefox" then you need only worry about "firefox".  The suggestions were given based on the vague info you gave.  And it was sufficient enough to restore firefox.

But if you say, "I sudo su'd and ran rm -fR /etc /usr/lib" THEN THAT is a different story.

---

### Post by tempus on 2009-12-30
> **3L33T said:**
> You are not telling the WHOLE SCENARIO.  If you claim "you borked up the system installing firefox" then you need only worry about "firefox".  The suggestions were given based on the vague info you gave.  And it was sufficient enough to restore firefox.

But if you say, "I sudo su'd and ran rm -fR /etc /usr/lib" THEN THAT is a different story.

Possibly!

---

### Post by tempus on 2010-01-03
Now that I reinstalled ubuntu 9.04 and all is functioning well my next question is this...is it possible to save a configuration so that re installs can be easily configured? :popcorn:

---

### Post by danastasio on 2010-01-03
>.< trying... to... ignore brain rot....


anyway, the only way to back up a configuration is to open your /home folder and copy all the hidden files to an external disk. just open nautilus and hit CTRL+H and you will see all of them.

---

### Post by underquark on 2010-01-03
What did you do, exactly?  If you can remember then there may be a straightforward remedy.  Or, what isn't working now that you would like to work?

---

### Post by oldos2er on 2010-01-03
> **tempus said:**
> Now that I reinstalled ubuntu 9.04 and all is functioning well my next question is this...is it possible to save a configuration so that re installs can be easily configured?

I recommend a separate partition for /home, which makes it simple to preserve one's files and settings. See [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

