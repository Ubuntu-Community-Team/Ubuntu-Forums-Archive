---
title: "QT Creator cannot find C++ library"
date: 2010-07-28
forum: General Help
---

### Post by dulanja on 2010-07-28
Hi all,

I installed Qt SDK for Linux/X11 on my Lucid. But when I try to write a simple program, Qt Creator cannot recognize the c++ headers.

Exact message when I used #include <iostream> : "iostream:No such file or directory". 

Seems it cannot find the C++ standard library headers. Also gives a similar error when I try to use the std namespace.

How can I resolve this? From where and how can I give the C++ headers to the Qt Creator.

I'm a newbie to programming on ubuntu. Appreciate your help.
Thanks :)

---

### Post by gmargo on 2010-07-28
Install the **libstdc++6-4.4-dev** package.

Here's one way to figure this out.  If you go to [http://packages.ubuntu.com](http://packages.ubuntu.com) then scroll down to the "Search the contents of packages" section.  Enter "iostream" in the keyword box and hit search.  That will give you all the packages with a file named "iostream".  In this case there are three realistic candidates: libstdc++6-4.{1,3,4}-dev.  The latest one, libstdc++6-4.4-dev matches the default gcc-4.4/g++-4.4 compiler.

---

### Post by orky7 on 2010-07-28
in Qt creator how are you writing the program i mean did you create a project and write the code or what?? since this type of error occur when you do not create projects, and simply write code to a c++ source file.

---

### Post by dulanja on 2010-07-29
> **gmargo said:**
> Install the **libstdc++6-4.4-dev** package.

Here's one way to figure this out.  If you go to [http://packages.ubuntu.com](http://packages.ubuntu.com) then scroll down to the "Search the contents of packages" section.  Enter "iostream" in the keyword box and hit search.  That will give you all the packages with a file named "iostream".  In this case there are three realistic candidates: libstdc++6-4.{1,3,4}-dev.  The latest one, libstdc++6-4.4-dev matches the default gcc-4.4/g++-4.4 compiler.

I installed it from synaptic. But no difference. :(

> in Qt creator how are you writing the program i mean did you create a  project and write the code or what?? since this type of error occur when  you do not create projects, and simply write code to a c++ source file. 	

Yep. I created a console project and writing in the main.cpp

---

### Post by orky7 on 2010-07-29
i just now tried in my qt-creator i go and create a project in "QT4 console application" then deleted the whole content of main.cpp but did not touch the .pro file and write a program and it is working. 

just a side note: better to program in anjuta or eclipse if you want to write c++ program, u can use qt for Gui dev.

---

### Post by dulanja on 2010-07-30
Finally it's solved :D I had to rename the 'g++-4.4' executable in /usr/bin to 'g++'. Working perfectly now! Thanks a lot gmargo.

> **orky7 said:**
> i just now tried in my qt-creator i go and create a project in "QT4 console application" then deleted the whole content of main.cpp but did not touch the .pro file and write a program and it is working. 

just a side note: better to program in anjuta or eclipse if you want to write c++ program, u can use qt for Gui dev.

Thanks for the help. I'm planning to do GUI development using Qt. Just tried a console app as the first step :)

---

