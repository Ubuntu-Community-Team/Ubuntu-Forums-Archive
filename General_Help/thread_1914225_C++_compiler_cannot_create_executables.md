---
title: "C++ compiler cannot create executables"
date: 2012-01-23
forum: General Help
---

### Post by rfbeck on 2012-01-23
Recently I tried to install a program starting with the command "./configure" . I got an error: "configure:3364: error: C++ compiler cannot create executables". 
   What's the deal with that, it's out of my league, but I was unable to continue with the "make" command.
   For the sake of curiosity I was trying to compile "Alien Arena".
_______
Robert

---

### Post by lisati on 2012-01-23
Do you have build-essential installed?

---

### Post by rfbeck on 2012-01-24
How do I go about getting that? Thanks.
______
Robert

---

### Post by rfbeck on 2012-01-24
Okay I got  build-essential and installed it. More progress seems to be made during the ./configure process.

Now though when I type "make" I get a message that says "make: *** No targets specified and no makefile found.  Stop."

What can this be about?
_______
Robert
Ubuntu novice

---

### Post by pbrane on 2012-01-24
You should look at the ./configure output for any errors. It sounds like your configure is not completing. What software are you trying to compile?

---

### Post by rfbeck on 2012-01-24
Well,now my ./configure is completing okay. I added the missing libraries. Now however,when I go to "make" I get the following errors:

"make[1]: Leaving directory `/home/robert/Downloads/alien-arena-7.53+dfsg/source'
make[1]: Entering directory `/home/robert/Downloads/alien-arena-7.53+dfsg'
make[1]: *** _No rule to make target `arena/motd.txt', needed by `all-am'.  Stop._
make[1]: Leaving directory `/home/robert/Downloads/alien-arena-7.53+dfsg'
make: *** _[all-recursive] Error 1_"

Oh boy. I have no clue what these errors are.
______
Robert
ps-I'm trying to install the latest version of Alien Arena

---

### Post by pbrane on 2012-01-24
I'm not sure why make wants to 'build' motd.txt. I would suggest you try this PPA to get alien-arena. It works for me, but it's only release 7.52 - [http://www.playdeb.net/updates/Ubuntu/11.10]("http://www.playdeb.net/updates/Ubuntu/11.10")

Where did you get the source? I'm using *svn://svn.icculus.org/alienarena/trunk* to see if I can build it.

---

### Post by rfbeck on 2012-01-26
I got the source from the Alien Arena web site. I downloaded it as a tar archive. 
specifically because it was there latest 7.53 version and I am obsessed with updates. I just am having trouble compiling the source. Ubuntu Software Center only has the 7.52 version.
Is there a solution? Where can I get the 7.53 version that will install in a more civilized manner?
______
Robert

---

### Post by rfbeck on 2012-01-26
Updated : I found an easy to install version packaged as a deb file at: [https://launchpad.net/ubuntu/precise/amd64/alien-arena/7.53+dfsg-1](https://launchpad.net/ubuntu/precise/amd64/alien-arena/7.53+dfsg-1).

So I used my deb package installer which sent it to software center   and it installed no problem. Except it doesn't work, I don't think version 7.53 of Alien Arena is ready for prime time. I'm gonna stick with ver 7.52 for now.
_______
Robert

---

