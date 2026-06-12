---
title: "KDevelop4 asks for cmake file in order to finish creating c++ project? what is cmake?"
date: 2010-01-04
forum: General Help
---

### Post by cgb223 on 2010-01-04
hey I'm a relative n00b to C++ but I have heard that KDevelop rocks so I am using it as my IDE. what does it mean when it wants me to find a cmake file? idk what that is lol, just got through the section on if statements on my book. where do i find this file? are there any good tutorials on the KDevelop4 Enviroment?

 I do not want to switch to a different IDE, I want to figure out KDevelop. 

thanks in advanced!

Charlie

---

### Post by gsmanners on 2010-01-04
CMake generates the makefile (which the compiler uses).

See the packages cmake and cmake-gui. You might want to get qt-sdk (Complete Qt Software Development Kit) just to be sure you don't miss something.

---

### Post by GameManK on 2010-01-10
Is it asking for the executable?  Install the cmake package and the default (/usr/bin/cmake) should work then.

If you're just learning the basics of C++ though, it might be more useful to use a basic text editor like kate and compile on the command line.  Once you start using multiple files in your project, move on to an IDE like KDevelop.

---

