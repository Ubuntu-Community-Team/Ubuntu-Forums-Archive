---
title: "I just broke everything again!"
date: 2009-07-06
forum: General Help
---

### Post by Blue Dolphins on 2009-07-06
I was installing a program from a deb file, and it said in order to complete installing, I had to run sudo apt-get install -f (DON'T type that, ever) and I the command line started listing off tons of programs that had successfully been deleted, I stopped the terminal, but the damage had already been done, error alerts were popping up nonstop, and it even deleted the program to turn off the computer.  

I'm using the live CD now, is there anyway to fix this, or atleast salvage the data and do a fresh install?  I have my entire CD collection on the harddrive, and don't want to spend an entire day ripping CD's.  I'm pissed, this isn't even the first time I accidently ruined Xubuntu from having no Idea what I'm doing.

---

### Post by philcamlin on 2009-07-06
does it even boot up to the 

login screen?

---

### Post by Blue Dolphins on 2009-07-06
It boots up, but into a command line, I guess I ruined the Desktop Environment too.  

I don't understand, I downloaded the .deb file from the debian repos, so I trusted it, but it tricked me in to deleting everything.

---

### Post by mbeach on 2009-07-06
Which file you were installing from. What was the deb package name?

---

### Post by Blue Dolphins on 2009-07-06
I was trying to install the newest version of perl-base.

---

### Post by jumbofishmeat on 2009-07-06
If you can access the hard drive from your Live CD then you can copy all of your necessary files over to a flash drive, but i would reccomend erasing the partitions and starting over after you are done there. Sounds like your system is royally screwed up, and doing a fresh install never hurt anyone. (It's a lot easier than a windows fresh install)

---

### Post by kerry_s on 2009-07-06
> **Blue Dolphins said:**
> I was trying to install the newest version of perl-base.

well there you go, ubuntu has a lot of pearl, if you update 1 you have to update all to match that version. rule of thumb is only go outside the repo if you absolutely have to.

---

### Post by Blue Dolphins on 2009-07-06
I've done plenty fresh installs before, I just hate spending all that time, deleting programs I don't use, installing programs I do use, installing the hundreds of updates after an install, installing and configuring plugins, ect.  

Atleast now I know never to run a command without looking up what it is first, even if debian told you to run it.

> **kerry_s said:**
> well there you go, ubuntu has a lot of pearl, if you update 1 you have to update all to match that version. rule of thumb is only go outside the repo if you absolutely have to.
I got 8.10 and even before 9.10, most packages were old, so I just got in the habit of always going to the debian repos, in about 4 months, this is the first time a deb didn't work perfectly.

---

### Post by kerry_s on 2009-07-07
> I got 8.10 and even before 9.10, most packages were old, so I just got in the habit of always going to the debian repos, in about 4 months, this is the first time a deb didn't work perfectly.

it's a bad idea to use debian debs on ubuntu, ubuntu does there own thing and it's set up to do it that ubuntu way.

have you tried debian testing? it just updates all the time, the stuff is not new new, but more updated than stable & safer than unstable, which is what ubuntu uses to build from.

---

### Post by 3rdalbum on 2009-07-07
> **Blue Dolphins said:**
> I got 8.10 and even before 9.10, most packages were old, so I just got in the habit of always going to the debian repos, in about 4 months, this is the first time a deb didn't work perfectly.

You've been very lucky in the past. With Debian, all packages assume that all other Debian packages are available. When you put a Debian package onto an Ubuntu system, it might be listed as "conflicts" with a version of a package shipped in Ubuntu. On Debian this makes perfect sense; for Debian that's an obsolete version that needs to be deleted; on Ubuntu it's the current package!

---

