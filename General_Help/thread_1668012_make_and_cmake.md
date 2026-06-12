---
title: "make and cmake"
date: 2011-01-15
forum: General Help
---

### Post by imaginashawn on 2011-01-15
So, I'm trying to get touchlib installed on my Maverick box and it seems I'm almost there and then the instructions I'm reading say the following and I'm stuck on the fifth line down because I've never used 'make' or 'cmake';

# Now compile touchlib:
# mkdir touchlib
# cd touchlib
# svn checkout [http://touchlib.googlecode.com/svn/trunk/](http://touchlib.googlecode.com/svn/trunk/) .
# cmake . (or “ccmake .” if you want a GUI)
# make
# Touchlib should now be ready to use.

What to do? :(

Thanks, Shawn

---

### Post by kn0w-b1nary on 2011-01-15
ccmake is a program that can be installed by typing this in terminal:
sudo apt-get install cmake-curses-gui
then type in terminal:
ccmake
it will spit out some info that might be helpful.

Hope this helps!

---

### Post by imaginashawn on 2011-01-15
cmake = cross platform build system ... o.k. got it. 

Why didn't I just type 'cmake' into the search box so I could go read the doc? Probably because I'm fighting a viral infection that's muddying up my brain. :p
[http://www.cmake.org/cmake/help/documentation.html]("http://www.cmake.org/cmake/help/documentation.html")
[http://www.cmake.org/Wiki/CCMake_2.0.6_Docs]("http://www.cmake.org/Wiki/CCMake_2.0.6_Docs")
Thanks know! 
Shawn

---

### Post by kn0w-b1nary on 2011-01-15
You are certainly welcome! :D

---

