---
title: "Newbie Question: How do I get started programming in Linux (terminal only)?"
date: 2010-07-29
forum: General Help
---

### Post by dpatel304 on 2010-07-29
I've been given an assignment for school, and we were supposed to set up a virtual machine and install Arch Linux to do our programming assignments.  I seem to have successfully installed Arch Linux and am able to log in as a 'root'.  All I am presented with is a terminal, which, I'm assuming, is enough to get started. 

I've only used Ubuntu a handful of times, so only having the terminal is a bit scary for me, and basically I need someone to point me in the right direction as to how I go from logging in as only the root to writing a program that replicates files (the programming part I should be able to do, I just have no idea how to get started with only a terminal).

Thanks in advance.

---

### Post by prodigy_ on 2010-07-29
What programming language are you going to use?

---

### Post by dpatel304 on 2010-07-29
> **prodigy_ said:**
> What programming language are you going to use?

C and C++

---

### Post by RabbitWho on 2010-07-29
Does this help?

[http://gcc.gnu.org/](http://gcc.gnu.org/)

---

### Post by prodigy_ on 2010-07-29
Well, you can use [GCC](http://en.wikipedia.org/wiki/GNU_Compiler_Collection) to compile your code. As for IDEs, there are [plenty of them](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B).

Why are you limited to using command line, by the way? Arch allows you to install a GUI (desktop environment) like any other Linux distro.

---

### Post by dpatel304 on 2010-07-29
> **prodigy_ said:**
> Well, you can use [GCC](http://en.wikipedia.org/wiki/GNU_Compiler_Collection) to compile your code. As for IDEs, there are [plenty of them](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B).

Why are you limited to using command line, by the way? Arch allows you to install a GUI, like any other Linux distro.

Thanks for the link.  I guess I'm not limited to the terminal, but since this is really only for a couple assignments, I'm okay with just going without the GUI.  Once I know how to set up a compiler, then it's basically just the same anyway, correct (I could probably get a prettier IDE with a proper GUI, I suppose).

---

### Post by nmaster on 2010-07-29
why are you required to use Arch?

---

### Post by dpatel304 on 2010-07-29
> **nmaster said:**
> why are you required to use Arch?

Not really sure, to be honest.  I never questioned it, and now I'm so far behind, that it would look silly to question it, as I have missed the first assignment so am already starting behind, which is why I'm asking these basic questions here.

I suppose Ubuntu would also get the job done just the same, and I'm at least somewhat comfortable with at least getting started with it.

---

### Post by jerenept on 2010-07-29
you can write the source code in nano, vi, etc, and save it with the extension ".c"

eg. myprogram.c

then gcc /path/to/myprogram.c

I think this is how it works.

---

### Post by dpatel304 on 2010-07-29
nvm

---

### Post by jerenept on 2010-07-29
check the Ubuntu Software centre.

Click "developer tools"
then "IDE's"

---

### Post by g00f on 2010-07-29
From the command prompt, use a text editor to create a file called project1.c.

I'm not sure what console mode text editors are available in arch, you'll have to figure that bit out.

In this file type something like:
```

#include <stdlib.h>
#include <stdio.h>

int main(int argc, char *argv[])
{
        printf("Hello world\r\n");

        return EXIT_SUCCESS;
}

```
Back at the command prompt compile it with a command like:
```

gcc project1.c -o project1

```

And run it with:
```

./project1

```

If you have the required "man page" packages installed, you can get help with command like:
```

man printf

```

The rest is up to you.

HTH

---

### Post by nmaster on 2010-07-29
> **dpatel304 said:**
> Since you brought it up, is there a preferred IDE for Ubuntu?  I've actually already got a virtual install of Ubuntu, so maybe I should just go with that.

i like to use emacs.  its technically just a text editor, but it makes a great IDE for many programming languages.  i've used it for scheme, java, c, python, bash, perl, etc.  its especially nice if you spend a little time getting used to the hotkeys and go completely from the command line.  you'll find that the keyboard is faster than the mouse (usually).

---

### Post by cinohpa on 2010-07-29
I'm a vim fan personally.

But if you just need something quickly for throwing together programs quickly, and you don't want to spend a lot of time getting used to a strange new text editor, just use gedit.

Also, if you are doing stuff in C/C++ and have some attachment to eclipse, you can just install the C/C++ plugins for that on linux...

---

### Post by Zorgoth on 2010-07-29
I would also recommend emacs.  It has a bit of a learning curve but it is an extraordinarily powerful tool capable of performing an astonishing array of functions.  And what's more, it has both a console and gui mode, so you can use the same editor for both.

---

### Post by Zorgoth on 2010-07-30
I recently posted a short introduction to emacs for beginners in the "Tutorials and Tips" section if you are interested:

[http://ubuntuforums.org/showthread.php?t=1542042](http://ubuntuforums.org/showthread.php?t=1542042)

---

