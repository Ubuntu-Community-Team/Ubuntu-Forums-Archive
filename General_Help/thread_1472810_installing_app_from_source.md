---
title: "installing app from source"
date: 2010-05-04
forum: General Help
---

### Post by nos09 on 2010-05-04
hey everybody i want to install pidgin from source code and i figured it out by reading a thread but now i have a question ... how exacly you install package from source code, ??

i mean i know that the command /.configure will make the "make" file and then i have to make " make install" to install the app. but how to deal with the dependency problem ? i asked my friend about it and he said why dont you use apt instead to install packages but what if i want to use distos like slackware !!!???

anyway that friend was not interested in helping me out and i m not expecting to. but can anybody answer this in detail or provide any document on this..

---

### Post by SnickerSnack on 2010-05-04
When you run the configure script, it will give output that tells you what dependencies you are missing.  Just pay close attention to any outputs from configure and make.

---

### Post by WorMzy on 2010-05-04
If you have unmet dependencies, then you need to install those first. Think of compiling a program like building a house. If you try to build a house without bricks, then you're not going to succeed. Get bricks first, then try to build the house. If you then discover that you don't have cement, then go and get cement, etc.

Btw, you should "make" before you "make install".

---

### Post by nos09 on 2010-05-04
now thats what i m talikin about - Dependancies .
when i asked that how to install pidgin they said download it and configure it but i got many errors about dependancy and then someone said that this is the code
 >  sudo apt-get build-dep pidgin

said that will install all dependancy, and i installed it in ubuntu.
but what if i m using slackware ? then how i m suppose to get those dependancies >?

---

### Post by oldos2er on 2010-05-04
Not to sound facetious, but if you have questions about Slackware, you might want to ask in the forums here: [http://www.linuxquestions.org/questions/slackware-14/](http://www.linuxquestions.org/questions/slackware-14/) 

Slackware has a package manager called slapt-get, which is somewhat similar to apt-get.

---

### Post by marshmallow1304 on 2010-05-04
> **nos09 said:**
> but what if i m using slackware ? then how i m suppose to get those dependancies >?

Maybe Slackware has a similar tool.  If not, you'll have to pay attention to the output of ./configure and install the dependencies it requests.

---

### Post by andrew.46 on 2010-05-05
Hi nos,

> **nos09 said:**
> but what if i m using slackware ? then how i m suppose to get those dependancies >?

Well a full installation of Slackware 13 will have Pidgin installed for you so this particular package does not need to be compiled :). In general though with Slackware you will be expected to find the dependencies *yourself *and this is considerably less drama than you might imagine. Have a browse through slackbuilds.org and you will get an idea of how the system works...

All the best,

Andrew

---

