---
title: "How to edit and recompile an application in ubuntu"
date: 2009-10-14
forum: General Help
---

### Post by emigrant on 2009-10-14
hi guys,
please forgive me if my question is weird.:(
though iv been using linux for sometime, since from the beginning i don't have any idea what editing a source code and recompiling it means.

can anyone please give me a tutorial on how to edit a program and recompile it in ubuntu.
for example, is it possible for me to edit the 'Gimp' application and change the splash screen to a custom image i made.
or is it possible for me to change the gimp tool box shape? (from rectacnge to circle etc...)

thank you very much in advance.:popcorn:

PS: in what language the applications in ubuntu are written? and what language is used for ubuntu itself.

thank you.

---

### Post by hal10000 on 2009-10-14
Usually you should only recompile a program if you miss functionality in the precompiled package. You will need the source code of the programm and therefor have to activate the source repositories with your package manager or download downlad the source code, e.g. from the developer's website.
As a non-programmer you can then usually edit the configure or make files in the source to  re-adjust paths or change some default-settings. The source code usually contains README and/or INSTALL text-files where you can get info about what you can change and how to install the program.

If you are a programmer and have the source-code of a programm (which is mostly written in the C programming language) you can of course change anything you like if you have the knollege, but if you plan to publish the changes you made, you have to pay attention to the licence under which the original program was distributed.

> can anyone please give me a tutorial on how to edit a program and recompile it in ubuntu
There are thousands, if not millions of sites where you can get help. Google is your friend.

---

