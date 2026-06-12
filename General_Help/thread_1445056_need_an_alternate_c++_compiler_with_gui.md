---
title: "need an alternate c++ compiler with gui"
date: 2010-04-02
forum: General Help
---

### Post by meself on 2010-04-02
i have started working through a c++ tutorial using the code::blocks compiler.  but now need to install the compiler on an additional machine with Ubuntu8.04 running on it.  unfotunately, the codeblocks.org website has been down for a few days now and i'm not sure if the repository is working either.  code::blocks is not showing up in synaptic on that machine and i am unable to retrieve the entire repository address string from my existing installation.  there was a "deb" or something at the beginning. and i'm not sure adding the reposiory would work if codeblocks is on the fritz anyway.

IS THERE AN OTHER ALTERNATE C++ COMPILER WIHT A GRAPHICAL USER INTERFACE THAT I CAN RETRIEVE FROM SYNAPTIC, AT LEAST UNTIL CODEBLOCKS.ORG WEBSITE COMES BACK TO LIFE?  i have g++, g++ 4.2, gcc, gcc 4.2, lib64gomp1, lib64stdc++6, libgomp1, etc., etc. installed.  but no alternative c++ compilers show up in my applications>programing menu.

---

### Post by meself on 2010-04-02
I found the alternate compiler that i need on another thread, "KDevelop".  It seems to work.

---

### Post by akakingess on 2010-04-02
Have you tried just running one of those programs by typing the name into the terminal, I am just now starting to learn C++ so haven't even begun to compile, but I have had applications not show up in the application menu and just typed them into the terminal and they have launched, that's about the only suggestion that I have for you.

Just saw the KDevelop message, usually means it was written for KDE instead of Gnome, and although some work both ways I would just be a little careful unless you are already running KDE instead of Gnome.  Just my 2 cents.

---

### Post by Vaphell on 2010-04-02
you confuse 2 different things - g++, gcc are compilers and their only role is to build a binary file from the source files.
Source file editing can by done by any text editor, but there are so called IDEs (Integrated Development Environment) that make the code editing more convenient. These environments under the hood call the compiler to do the work, but they are not compilers themselves.

---

### Post by meself on 2010-04-03
thank you, akakingess.  you are correct and KDevelop does not, in fact, seem to function in Gnome as I had thought.  fortunately, codeblocks.org is now back online and I am able to install code::blocks on my other machine.

i have had no success typing the names of programs that show up in synaptic into terminal to open them, but i'm ok for the moment because code::blocks is available again.

Vaphell, i suspected that was the case, but since i have no experience running the compilers from command line in terminal if that's possible, for incorrect terminology, i was actually looking for an alternate ide.  still have not located one for gnome but not needing it at the moment because code::blocks is accessible again.

---

### Post by Chronon on 2010-04-03
Maybe Geany will meet your needs.

---

### Post by akakingess on 2010-04-03
> **meself said:**
> thank you, akakingess.  you are correct and KDevelop does not, in fact, seem to function in Gnome as I had thought.  fortunately, codeblocks.org is now back online and I am able to install code::blocks on my other machine.

i have had no success typing the names of programs that show up in synaptic into terminal to open them, but i'm ok for the moment because code::blocks is available again.

Vaphell, i suspected that was the case, but since i have no experience running the compilers from command line in terminal if that's possible, for incorrect terminology, i was actually looking for an alternate ide.  still have not located one for gnome but not needing it at the moment because code::blocks is accessible again.

Just to suggest another source, when I actually have code writing issues, I also visit DevShed (I believe it is just devshed.com) you can just google Developer Shed and it should take you there, and there are sections for every coding language and even some sub-sections if I remember correctly, but just wanted to turn you onto yet another source to check out and chat with some other writers?...

---

