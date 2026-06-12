---
title: "NEWB question, installing programs from source?"
date: 2010-09-07
forum: General Help
---

### Post by ICANSEEYOU7687 on 2010-09-07
Im trying to install mupen64plus, but to be honest, everything i have installed is from the package manager.  I have no idea how to do this through the terminal.

But I tried installing the mupen64plus from the package manager, and everytime I open a rom, mupen64plus closes and doesnt load anything....

That version was 1.5, and I downloaded 1.99.3 or whatever it is from the mupen site, but I cant get the sucker to install.

There is a install.sh file which I chmod +x too.

I then tried, ,/install.sh, make install...

there is a mupen64plus file, that when I try to run, it yells at me.

Im so lost...

---

### Post by MilesTails on 2010-09-08
Installing from source can be tricky...is there a readme file in with the sources?

Usually when you build something from source it goes: ./configure then make then make install, but it depends on the software.

Also make install needs to be run as root.

Hope that helps, read the readme, and if there is an install text file read it as well, you should find all the info you need

---

### Post by bodhi.zazen on 2010-09-08
Read the documentation. I do not install applications that are poorly documented.

1. Go to the home page of your application, read the documentation.

2. Read the README.

Install the dependencies.

See also : [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Otherwise if you have a specific question at a specific step, ask. Be sure to included links to the project, documentation.

---

