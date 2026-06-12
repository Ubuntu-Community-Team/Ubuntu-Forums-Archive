---
title: "Compiler"
date: 2010-03-19
forum: General Help
---

### Post by Colo2 on 2010-03-19
Hey people

I was under the impression that linux comes with a compiler.. What is it called and how do I use it? I seem to remember someone telling me it was called "g" but maybe I dreampt it.

Thanks ;)

Tom

---

### Post by nothingspecial on 2010-03-19
g++ for c++

---

### Post by Colo2 on 2010-03-19
Hey
Thanks for the reply. 
How do I use it? sudo g and sudo g++ are unknown commands.

Thanks

Tom

---

### Post by srs5694 on 2010-03-19
First, there's no need to use "sudo" when compiling your own programs, or even those you've downloaded from somewhere and extracted into your home directory so that you own them. In general, it's best to minimize your use of sudo, since that command gives you root privileges, and "root privileges" means (among other things) "the chance to do very very serious damage to your computer."

Second, there are many different compilers available for different languages. The g++ compiler compiles C++ and gcc compiles C. These are the most commonly used ones. Which you use depends on what sort of software you're compiling. If you're compiling something you downloaded and want to compile locally, you should read any README or similar files that came with it. You might not use gcc or g++ directly; it may be that you'll need to use a program called "make" or some other tool.

Third, if you need to know how to write a program in C, C++, or any other language, you won't get a good idea from a single forum thread; that's a *very* complex topic. I recommend you go to a library or book store and get a good book on the topic. The programming books I've got are rather old, so I can't recommend any specific current titles. There are also, of course, Web sites on the topic. Try Googling to find them.

Finally, if you get a "command not found" error, chances are the software isn't installed. (Ubuntu comes with lots of stuff that's not installed by default.) Use apt-get (text-mode) or Synaptic (GUI) to install it. Using apt-get, you'd type "apt-get install gcc" or "apt-get install g++". I believe there's a meta-package that will install a bunch of programming tools, but I don't recall its name offhand.

---

### Post by Colo2 on 2010-03-19
thank you for your help :)

Yeah, I am following online tutorials for c++, I just needed the compiler to compile my scripts as I go along
 
Thanks for the info :)

---

### Post by Iowan on 2010-03-19
"Some day" I'll get around to compiling on Linux. The [Compiling]("https://help.ubuntu.com/community/CompilingSoftware") help page is more for packages, but does touch on the **build-essential** package. 
There's also a [Programming]("http://ubuntuforums.org/forumdisplay.php?f=39") subforum that might provide extra information - there are some helpful-looking stickies at the top (which I haven't read yet...).

---

### Post by nothingspecial on 2010-03-19
```
sudo apt-get install build-essential
```

```
g++ *[COLOR="Lime"]c++program[/COLOR]* -o [COLOR="Blue"]name_you_want_to_call_the_compiled_program[/COLOR]
```

---

