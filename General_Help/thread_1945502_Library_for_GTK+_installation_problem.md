---
title: "Library for GTK+ installation problem"
date: 2012-03-23
forum: General Help
---

### Post by edw999 on 2012-03-23
Sorry Newbie Problem!!!

I am running Ubuntu 11.04 classic with compiz configured and cairo-dock installed and everything is working perfectly!!!
However, I have the following program showing in my Update Manager:

[COLOR=Red]"Other updates (LP-PPA-webkit-team)
Web content engine library for GTK+
libwebkitgtk-1.0-0 (Size: 6.0 MB)"[/COLOR]

and I can neither tick it for installation nor do I know what this program is for!
I searched the Web for GTK and think that this facilitates the installation of programs  but frankly I am not aware this program is doing!

So my question is: 
1) should I ignore it (which I hate because I like to keep my Ubuntu nice and clean)
2) delete AptURL because this installed program is mentioning GTK+ as well and if I do not need the library maybe I also do not need AptURL????  But of course ignorant as I am I have no idea if this would break anything?

Any idea or suggestion highly appreciated!!!
Many greetings!!!!

---

### Post by ajgreeny on 2012-03-23
It looks as if you are trying to use a ppa repository that is not working, for whatever reason.

Go to System >Administration >Software sources and in the second tab you should find a listing for webkit ppa, which you can temporarily disable.  Then refresh the repos and the problem will go away.

I have no idea what was in the repository, not if you really need it, but as it is not working, that is a superfluous question;  you can't use it at the moment, so disable it.  Try it again in a few days if you want by reversing what you did this time.

---

