---
title: "Configuring, making, building"
date: 2011-05-16
forum: General Help
---

### Post by abedayyad on 2011-05-16
Hello, 

I am running Ubuntu 10.04 (lucid) and using KDE. 

I was in the process of installing GSL (GNU Scientific 
Library), and so downloaded all the files, a long, long time ago. I went into the relevant folder and tried to configure, as per the instructions, when, at the end, I get the following: 

config.status: creating gsl/Makefile
config.status: error: cannot find input file: gsl/Makefile.in

When I look in the same folder although, there is indeed a Makefile.in as well as a Makefile.am. 

Reassured that the files are there, I then go to "make", only to get: 

make: *** No targets specified and no makefile found. Stop. 

So how is it that I am being told that there is no Makefile when I can see it there when I type in ls? Have I maybe not installed one of the other requirements, like maybe a compiler? I do have a C compiler installed, which seems to be working, and I have also installed build essentials. 

Not sure what else might be the problem. 

Many thanks in advance for your help.

---

### Post by gsmanners on 2011-05-16
Any particular reason you're building from source rather than just using apt-get install [gsl-bin]("http://packages.ubuntu.com/lucid/gsl-bin")?

---

### Post by andrew.46 on 2011-05-16
Would it be easier to use the repository version? Unless you are after the latest version Lucid has this:

GNU Scientific Library (GSL) -- binary package
[http://packages.ubuntu.com/lucid/gsl-bin](http://packages.ubuntu.com/lucid/gsl-bin)

Different matter I guess if you are after the latest version, I see GSL-1.15 that came out a few weeks ago...

---

### Post by abedayyad on 2011-05-16
Thanks gsmanners, it's very nice of you. I didn't know there was something in the repositories, not sure why I didn't even check ... on the other hand, I'm a bit worried that this has shown up something a bit deeper. 

Thanks again!

---

### Post by abedayyad on 2011-05-16
Thank you sir!! I've gone and installed gsl from the repositories, but still unsure about what the underlying problem is ...

---

