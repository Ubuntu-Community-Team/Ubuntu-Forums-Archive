---
title: "programming"
date: 2006-01-25
forum: General Help
---

### Post by njzillest on 2006-01-25
I want to learn to program and create webpages. What should i start out with? i currently have a book from the dummies corp for C/++. SHould i learn HTML first? How long will it take me? is there any easy to use programs that i can find in the apt-get or synaptic package manager?

thanx for the help,
Adel

---

### Post by audax321 on 2006-01-25
I wouldn't jump into C/C++ too fast. I tried to and it was difficult. Instead, I'm now learning Python which is pretty straight-forward and then moving onto C++ once I'm good enough to write Python GUI apps. I just got some books from my local library.

As far as HTML goes, its not really a programming language but more of a scripting language. In any case just search Google for 'html tutorial' and it should bring up a lot of information. Once, you get the handle of html, look into CSS. I just learned that a few weeks ago and it makes maintaining a large website almost too easy.

(Also for future reference, this should probably be posted in the Programming Talk section: [http://www.ubuntuforums.org/forumdisplay.php?f=39](http://www.ubuntuforums.org/forumdisplay.php?f=39))

---

### Post by njzillest on 2006-01-25
so you suggest python then c/c++? is python easier and is it alot like c++? 


I know html is used for web editing, i was just wondering if it is easy, and if it would help me on my jounrey to mastering c++

I can get a python app from synaptic?? where can i get help for it?

---

### Post by glinsvad on 2006-01-25
> I want to learn to program and create webpages. What should i start out with?
Which skill do you need the most right now? Personally I'd recommend getting down with C/C++ rightaway - it may take a while, but once you've learned it, moving on to HTML and Java is pretty simple.

I'll put it like this:
HTML: learn how to wash a car and change oil on it
C/C++: learn how to build your own car

> i currently have a book from the dummies corp for C/++
That will do just fine for now. Basically you just need an introdution to declaring variables, implementing if/else-structures and for/while-loops and calling functions.

> How long will it take me?
I started out with a 2-inch thick "Teach yourself C/C++ in 21 days" which does NOT actually take 21 days to complete... the thing is, that you will spend a lot more time just programming for the fun of it. 

> is there any easy to use programs that i can find in the apt-get or synaptic package manager
Yes, on GNOME open a terminal and type:
```
sudo apt-get install build-essential
```

Now, to compile your code (filename: hello.c)
```
g++ hello.cpp -o hello
```

Finally, to run it:
```
./hello
```

---

### Post by njzillest on 2006-01-25
njzillest@belkin:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
njzillest@belkin:~$ g++ hello.cpp -o hello
g++: hello.cpp: No such file or directory
g++: no input files


I dont know what this is. I never downloaded the app..? if you cant help me with this.. then is there any other good C/++ programm?

what is python used for anyway?

---

### Post by glinsvad on 2006-01-25
> I dont know what this is
Okay, maybe I went a bit too fast...

When you have written your first C/C++-program, say something like:

```

#include <iostream.h>
int main(int argc, char **argv)
{
cout << "Hello" <<endl;
return 0;
}
```

...you save it in a file called hello.cpp and compile it with the command:
```
g++ hello.cpp -o hello
```

Then you can run your own creation as:
./hello

---

### Post by era86 on 2006-01-25
I recommend learning C/C++ first because it is a good introduction to programming. It is a well rounded introduction and can open doors to other object oriented languages. As far as html goes, it is fairly easy to learn and won't take long once you know the basics of C/C++, so you can save it for later. ;) C/C++ is a good start for programmers.

I also recommend Anjuta as an IDE. You can get it using apt-get ( although I don't know the exact name )

---

### Post by njzillest on 2006-01-25
thanx guys for the help :)

---

