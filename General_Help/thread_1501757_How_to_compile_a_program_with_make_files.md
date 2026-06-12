---
title: "How to compile a program with make files?"
date: 2010-06-04
forum: General Help
---

### Post by OpressedCalamity on 2010-06-04
Hey, I'm a first time ubuntu user.
I've picked up the basics I guess
I've been trying to compile a program
With the make file and i'm not completly sure how to do that
Please help thanks! ^^

---

### Post by VCoolio on 2010-06-04
Do you really need to compile it? First check the repos, then check if there is a third party repo that has it (on launchpad.net), then check the homepage of what you're installing to check if there is a .deb file. 
The normal thing to compile is ./configure, make, sudo make install (sometimes you'll need ./autogen.sh first to create the build files), but also sometimes there is a python setup.py file or other installing methods like waf are used. Downside of all this is that your package manager is not aware of what you're installing. So use [checkinstall](https://help.ubuntu.com/community/CheckInstall) instead. Also read. Read man pages, README files, etc. And [this]("https://help.ubuntu.com/community/CompilingSoftware").

---

### Post by OpressedCalamity on 2010-06-05
Yes i'm sure i have to compile it
Now I get autoheader failed.

---

### Post by VCoolio on 2010-06-05
This is too little information. Post a link to what you're compiling; also post the error output here (between [code ][/code] tags). Do you have all dependencies you need?

---

### Post by OpressedCalamity on 2010-06-06
[http://mac-on-linux.sourceforge.net/](http://mac-on-linux.sourceforge.net/)


And heres the output.

==================================================
 Invoking autoheader and autoconf.
./autogen.sh: 20: autoheader: not found
autoheader failed
jacob@jacob-desktop:~/Desktop/mol-0.9.72.1$ ./autogen.sh
==================================================
 Invoking autoheader and autoconf.
./autogen.sh: 20: autoheader: not found
autoheader failed
jacob@jacob-desktop:~/Desktop/mol-0.9.72.1$

---

### Post by doorknob60 on 2010-06-06
sudo apt-get install build-essential

---

### Post by OpressedCalamity on 2010-06-08
I will try that, Thanks!

---

### Post by OpressedCalamity on 2010-06-08
Tryed that, it seems its already at its latest version.
Output was

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

---

### Post by oldos2er on 2010-06-08
Did you install its dependencies? [http://mac-on-linux.sourceforge.net/wiki/index.php/Installation_Instructions](http://mac-on-linux.sourceforge.net/wiki/index.php/Installation_Instructions)

---

### Post by OpressedCalamity on 2010-06-08
I'm still kind of new to linux. I don't completly understand how to do this :/

---

### Post by oldos2er on 2010-06-09
You can just copy and paste the apt-get install command into a terminal; you will need to use "sudo" e.g. "sudo apt-get install..."

---

### Post by OpressedCalamity on 2010-06-09
Screw this.

---

