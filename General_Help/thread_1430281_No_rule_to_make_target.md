---
title: "No rule to make target"
date: 2010-03-15
forum: General Help
---

### Post by ovu on 2010-03-15
[FONT=monospace]hi guys
im a bit of a noob but have been looking into compiling in ubuntu, ive done some research on the internet and think i have installed all the items required to compile in ubuntu

my problem is when trying to use the make command

me@me-laptop:~$ make -f openwebspider-07
make: openwebspider-07: No such file or directory
make: *** No rule to make target `openwebspider-07'. Stop



any suggestions will be appreciated




[/FONT]

---

### Post by Mr Nemo on 2010-03-15
What are you trying to compile and did you use ./configure beforehand? Are there install instructions that came with the program youre trying to compile?

---

### Post by ovu on 2010-03-15
I am trying to compile a web crawler by the name of "open webspider" i have read the documentation for it which says

"Unpack the package and compile it (with “make” under linux and with MS Visual C++ under windows)
Now you can try to execute OpenWebSpider with (under linux):

$ ./openwebspider "


 i was not aware that ./configure was required will try that now


thanks

---

### Post by ovu on 2010-03-15
no luck im afraid

me@me-laptop:~$ ./configure
bash: ./configure: No such file or directory

anyone have any ideas where im going wrong???

---

### Post by t0p on 2010-03-15
Very good tutorial on compiling source for Ubuntu [here]("https://help.ubuntu.com/community/CompilingEasyHowTo").

---

### Post by ovu on 2010-03-15
@t0P

thanks but ive allready used that as a starting point. any other suggestions?

---

### Post by mcduck on 2010-03-15
Make sure you are actually running the commands in the same directory where you have the source files... ;)

---

### Post by ovu on 2010-03-15
i think its almost worked just need help explaining whats happened here (i.e the error 1)



code:
me@me-laptop:~$ make -C /usr/local/src/
make: Entering directory `/usr/local/src'
gcc openwebspider-0.7.c -o openwebspider `mysql_config --cflags --libs` -lpthread -ldl -rdynamic -Wall -O2
In file included from openwebspider-0.7.c:88:
thread.h: In function &#8216;mainThread&#8217;:
thread.h:57: warning: cast from pointer to integer of different size
In file included from openwebspider-0.7.c:88:
thread.h: In function &#8216;CreateThreads&#8217;:
thread.h:418: warning: cast to pointer from integer of different size
thread.h: In function &#8216;CreateServerThread&#8217;:
thread.h:438: warning: cast to pointer from integer of different size
In file included from openwebspider-0.7.c:97:
server.h: In function &#8216;StartOWSServer&#8217;:
server.h:47: warning: cast from pointer to integer of different size
gcc -g -c modules/regexFilter/regexFilter.c
gcc -g -shared -W1,-soname,regexFilter.so.0 -o modules/regexFilter/regexFilter.so regexFilter.o -lc
/usr/bin/ld: regexFilter.o: relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
regexFilter.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [mod_regexfilter] Error 1
make: Leaving directory `/usr/local/src'

---

