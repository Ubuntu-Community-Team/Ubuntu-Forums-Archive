---
title: "Newbie's GNU C/C++ question"
date: 2012-02-29
forum: General Help
---

### Post by chenxinghao on 2012-02-29
I installed Ubuntu 11.10 in Jan. with the default settings and dual-boot with Windows XP Pro. The default setup also has somehow installed a GNU C compiler and I followed suggestions in this forum and installed the C++ compiler as well.

I am migrating several of my old C programs onto my Ubuntu box. With very few changes I am able to recompile the old C codes with GNU C (gcc). I ran the programs to compare the results with old records and all seem to match, except the CPU time usage.

Recompilation these old C codes with GNU C (gcc) did not generate any error or warning.

I wrote these C codes many years ago on Sun Microsystems and HP computers and  the CPU time usage numbers were used for comparing computation efficiencies.

In the top header file I have the following:

#ifdef SUNUX
#include <sys/time.h>
#include <sys/resource.h>
#endif

#ifdef HPUX
#include <sys/times.h>
#include <sys/unistd.h>
#endif

My question is what are the corresponding header files on Ubuntu+GNU C for time.h and results.h of Sun-Solaris and times.h and unistd.h of HP-UX?

Without these header files, all CPU time usage numbers I got are 0s.

---

### Post by hawkmage on 2012-02-29
Try looking under /usr/include/x86_64-linux-gnu or /usr/include/i386-linux-gnu depending on what hardware platform you are running.  

In that directory you will find the sys directory with the header files you are looking for.  Take a look at them to see which ones implement the functions/methods you are calling.

---

### Post by chenxinghao on 2012-03-01
In /usr/include on Ubuntu, there are time.h, times.h and unistd.h, but not resource.h.

---

### Post by imachavel on 2012-03-01
I'm in the gedit right now, I saved your code as a ccode.c file, in a directory called C. Now I didn't know

# actually worked for anything except making notes. I know little about code writing, in python this would be called .py, and it would look more like

def
   :()

or something or another

I don't know what you are writing this code for, so if I was going to compile it, I suppose I would 

gcc -o -(another tag I forgot) 

now I would gcc -o the name of the current file code.c and then the other tag would define the name of the new code file, correct? Sorry I try and keep up with this I want to contribute to open source, and man is there a ton of stuff you can write or what? I'm currently learning html tags such as

<body>

<header>

<p>

</p>

I'm pretty newbish at writing code. html is only a pain because of other files associated with tags you use to include images, and honestly there are thousands of different color and font formats, I'm using an ide called bluefish editor. I like to test an html page in local host first, which is in /var/www

I am using apache as the back end, I got an html page in there right now, and I access it by typing in the i.p. of my pc, then it opens that page. I have no url name for the file, I suppose index.html would work, no it doesn't. I suppose I would need dhcp or dns service running to open the page based on the name of the file? Or just another back end process like sql or something?

---

### Post by imachavel on 2012-03-01
how do I get root control while browsing the GUI again? I thought I typed gksu into the terminal, but that only allows me to execute a program as root. I'm on the right track though right?

here we are for python:

print "Hello, World!" 

save it as helloworld.py

then open it:

python helloworld.py
Hello, World!

a little too simple, I'm not even sure how the argument is defined, since there is no def
or
:()

for c I was using this:

[http://www.cs.cornell.edu/courses/cs113/2006fa/Write_Your_First_C_Program.html](http://www.cs.cornell.edu/courses/cs113/2006fa/Write_Your_First_C_Program.html)

but forgot how to compile it


gcc -o hello hello.c
gcc: error: hello.c: No such file or directory
gcc: fatal error: no input files
compilation terminated.
danel@danel-Dimension-4700:~$ ./hello
bash: ./hello: No such file or directory

I need another tag -o should only find the input file, there should be another tag that lists the name of the new file once it's compiled so the binary can be addressed

---

