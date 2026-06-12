---
title: "error when using ifort"
date: 2010-01-17
forum: General Help
---

### Post by subjugater on 2010-01-17
```

mike@mike-desktop:~/study/jiang/codes/fortran/rational_part/ffttest$ ifort my_precision.f90
/opt/intel/Compiler/11.1/064/bin/ia32/fortcom: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ifort: error #10273: Fatal error in /opt/intel/Compiler/11.1/064/bin/ia32/fortcom, terminated by 0x7f

```

I just installed the intel fortran compiler. When trying to compile a simple test program, I encountered the above error. Anybody can tell me how to solve this problem? Thanks a lot.

---

### Post by subjugater on 2010-01-17
bump up

---

### Post by subjugater on 2010-01-17
bump up again~

---

### Post by beren.olvar on 2010-01-17
Are you sourcing the necessary files?
if you use bash, there should be a line like

. /opt/intel/Compiler/11.1/056/bin/intel64/ifortvars_intel64.sh

in your .bashrc file.
Note the dot ( . ) at the beginning and also you should look for the path of your installation. It is probably a bit different. Also be aware that I am using the 64 bits compiler, if you use the 32 bit one, the path will be slightly different.

after adding that (with the necesary changes), start a new terminal and try again.

Cheers!

edit: other possibility is that you are missing some dependencies. Check if the package "libstdc++" exist in your distribution and that it is installed. I am currently not using ubuntu, so I do not know what the exact name is for the package, but googling a bit should be enough.

---

### Post by subjugater on 2010-01-17
> **beren.olvar said:**
> Are you sourcing the necessary files?
if you use bash, there should be a line like

. /opt/intel/Compiler/11.1/056/bin/intel64/ifortvars_intel64.sh

in your .bashrc file.
Note the dot ( . ) at the beginning and also you should look for the path of your installation. It is probably a bit different. Also be aware that I am using the 64 bits compiler, if you use the 32 bit one, the path will be slightly different.

after adding that (with the necesary changes), start a new terminal and try again.

Cheers!

edit: other possibility is that you are missing some dependencies. Check if the package "libstdc++" exist in your distribution and that it is installed. I am currently not using ubuntu, so I do not know what the exact name is for the package, but googling a bit should be enough.

Buddy, thanks a lot. Your explanation and suggestion are very helpful. In fact, following the suggestion in the thread below,

[http://ubuntuforums.org/showthread.php?t=1082782&highlight=ifort]("http://ubuntuforums.org/showthread.php?t=1082782&highlight=ifort")

I had added
```
PATH="/opt/intel/Compiler/11.1/064/bin/ia32:$PATH"
export PATH
LD_LIBRARY_PATH="/opt/intel/Compiler/11.1/064/lib/ia32:$LD_LIBRARY_PATH"
export LD_LIBRARY_PATH
```
in the .bashrc file and have "sourced" it before I posted this thread. Is there anything wrong with the above lines? Thanks.

---

### Post by beren.olvar on 2010-01-18
Sourcing (dotting) the file ifortvars_intel64.sh takes care of the extra lines you have added. I don't know if having them repeated can cause any problem, but in any case you should try commenting them out, just to see if something changes.
If you have also installed the dependencies listed in [http://ubuntuforums.org/showthread.php?t=1082782&highlight=ifort](http://ubuntuforums.org/showthread.php?t=1082782&highlight=ifort) , particularly libstdc++6, then I am running out of ideas.
May be you could try reinstalling, and see if the installer complains about something.

post back your results!
good luck! :)

---

### Post by subjugater on 2010-01-18
> **beren.olvar said:**
> Sourcing (dotting) the file ifortvars_intel64.sh takes care of the extra lines you have added. I don't know if having them repeated can cause any problem, but in any case you should try commenting them out, just to see if something changes.
If you have also installed the dependencies listed in [http://ubuntuforums.org/showthread.php?t=1082782&highlight=ifort](http://ubuntuforums.org/showthread.php?t=1082782&highlight=ifort) , particularly libstdc++6, then I am running out of ideas.
May be you could try reinstalling, and see if the installer complains about something.

post back your results!
good luck! :)

Buddy, thanks for your post. I get 3 questions.

1. By the file ifortvars_intel64.sh, which file you are referring to? In which folder? I am lost when stepping into those folders, 'coz I found that thousands of files in many different places share almost the same name like "ifortvars_intel64.sh".

2. To be frank, I even don't know if I installed the right version. I know that my desktop has two cores (cpus). But my friend told me that this doesn't mean that the computer is of 64-bit architecture and the architecture of the computer also depends on the choice I made when install the ubuntu. Is it correct? Is there any way for me to test on my desktop to see which architecture I am using?

3. Is there any tutorial can help me out with the fundamental of the structure of ubuntu? Perhaps I need to learn more about the underlying structure of linux, if I intend to understand the installation procedure of any software, like ifort.

Sorry, if my questions are dumb or naive. Thank you.

---

### Post by beren.olvar on 2010-01-18
In my first post I told you to add the following line to your .bashrc file

. /opt/intel/Compiler/11.1/056/bin/intel64/ifortvars_intel64.sh

That file will automatically change your PATH and LD_LIBRARY_PATH as needed.
The actual route of the file will change according to your version and architecture. But should be something very similar.

To get your architecture you can write in a terminal

uname -a

and if something like x86_64 appears, then you have a 64bit operating system, otherwise (only something like x86) you have a 32bit OS.

After finding that out, you should try reinstalling the compiler to make sure you have the right version for you (the compiler has a 64 and 32 bit versions, you can choose at install time). 

Finally, you can certainly read some manuals and tutorials, but I think a good way to learn how to use linux is just to play around, make mistakes and learn how to fix them :) know that the "man" command is very helpful and come to the forums when you run out of clues :)

Let us know whether your compiler is working or not

cheers :)

---

### Post by subjugater on 2010-01-19
> **beren.olvar said:**
> In my first post I told you to add the following line to your .bashrc file

. /opt/intel/Compiler/11.1/056/bin/intel64/ifortvars_intel64.sh

That file will automatically change your PATH and LD_LIBRARY_PATH as needed.
The actual route of the file will change according to your version and architecture. But should be something very similar.

To get your architecture you can write in a terminal

uname -a

and if something like x86_64 appears, then you have a 64bit operating system, otherwise (only something like x86) you have a 32bit OS.

After finding that out, you should try reinstalling the compiler to make sure you have the right version for you (the compiler has a 64 and 32 bit versions, you can choose at install time). 

Finally, you can certainly read some manuals and tutorials, but I think a good way to learn how to use linux is just to play around, make mistakes and learn how to fix them :) know that the "man" command is very helpful and come to the forums when you run out of clues :)

Let us know whether your compiler is working or not

cheers :)

Buddy, thanks for your post. I followed what you told and have already copied and pasted that line in the .bashrc file. Unfortunately, it doesn't work.

I checked the architecture of my desktop by using "uname". The answer given by the terminal is:
```
Linux mike-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

```

So this means that my system is of 32-bit, right? If this is the case, which version of the ifort compiler on the following webpage should I install? Is the last choice "Redistributable Libraries" useful for me?

[https://registrationcenter.intel.com/RegCenter/RegisterSNInfo.aspx?sn=NB3L-KVRSG5B2&EmailID=nullcline%40hotmail.com&Sequence=975596]("https://registrationcenter.intel.com/RegCenter/RegisterSNInfo.aspx?sn=NB3L-KVRSG5B2&EmailID=nullcline%40hotmail.com&Sequence=975596")

Thank you sooooooooooooooooooo much for your help along this thread. I really appreciate.

---

### Post by beren.olvar on 2010-01-21
Sorry for the delay in my reply.

Yes, you have a 32 bit OS. You should install the IA-32 version and I think the Redistributable Libraries are not needed unless you want to redistribute your executables.

I hope you can now have the compiler running. 
Post back your results!

cheers!

---

### Post by dave00001 on 2010-01-22
I am getting some really weird errors.  I have ifort installed, and when I run a (very simple) code the errors pile up real high, then the program exits.  

for example, I have a program hello.f95:

program hello
write(*,*) 'hello world'
end program hello

This is the output:

dave@dave-laptop:~/Desktop$ ifort -hello hello.f
: error #5149: Illegal character in statement label field  [p]

: error #5149: Illegal character in statement label field  [r]

: error #5149: Illegal character in statement label field  [o]

: error #5149: Illegal character in statement label field  [g]

: error #5149: Illegal character in statement label field  [r]

: error #5118: First statement in file must not be continued

hello.f(2): error #5149: Illegal character in statement label field  [w]
write(*,*) 'hello world'
^
hello.f(2): error #5149: Illegal character in statement label field  [r]
write(*,*) 'hello world'
-^
hello.f(2): error #5149: Illegal character in statement label field  [i]
write(*,*) 'hello world'


...................

and so on, until too many errors are reached...

What gives??

Note - I also have gfortran installed and the same thing happens there too.

---

### Post by beren.olvar on 2010-01-23
Hey!

good it is working now
try 2 things:
instead of 
ifort -hello hello.f
use 
ifort -o hello hello.f90

note the -o and that the filename should end with .f90, accordingly to the man page
([https://wiki.fysik.dtu.dk/dacapo/Installation?action=AttachFile&do=get&target=ifort.html](https://wiki.fysik.dtu.dk/dacapo/Installation?action=AttachFile&do=get&target=ifort.html))


hope it works!

---

### Post by dave00001 on 2010-01-23
Worked like a charm.  thanks.

---

### Post by niziris on 2010-10-11
@beren.olvar and @dave00001

THANKS PPL!!! your discussion also helped me...I installed intel couple months ago but I hade same problem as dave00001 and now 

> Worked like a charm

Thanks!! :KS

---

### Post by copross65 on 2011-04-15
Hey guys I dont get the PATH stuff. When I installed the installation program told me to do

source opt/intel/bin/ifortvars.sh or compilevars.sh or something like that 

so I just typed that in tha command line and done I got iFort..

and then  tried with the hello world progra, typing

$ifort -o name_output name_file.f90

and then

$./name_output

and done got the hello world message

Please someone explain me what is the PATH in bashrc thing for....

And something else Im trying to add  the cuba library to use it . follow the simple steps:
./configure
make

but then when I run my complex .f90 file it shows: undefined reference to Cuhre (btw, cuhre is a library within the library cuba :s or in simple words cuba is made of 4 libraries for complex integrations) 

WHYYYY WHYYYY is an undefined reference:(

---

