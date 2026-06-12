---
title: "Trying to Make Y86 Simulator for School Work - tk.h Not Found"
date: 2012-02-12
forum: General Help
---

### Post by Dan Again on 2012-02-12
I am trying to make a Y86 simulator using the following makefile...

```
# Comment this out if you don't have Tcl/Tk on your system

GUIMODE=-DHAS_GUI

# Modify the following line so that gcc can find the libtcl.so and
# libtk.so libraries on your system. You may need to use the -L option
# to tell gcc which directory to look in. Comment this out if you
# don't have Tcl/Tk.

TKLIBS=-L/usr/lib -ltk8.5 -ltcl8.5

# Modify the following line so that gcc can find the tcl.h and tk.h
# header files on your system. Comment this out if you don't have
# Tcl/Tk.

TKINC=-isystem /usr/include/tcl8.5

##################################################
# You shouldn't need to modify anything below here
##################################################

# Use this rule (make all) to build the Y86 tools. The variables you've
# assigned to GUIMODE, TKLIBS, and TKINC will override the values that
# are currently assigned in seq/Makefile and pipe/Makefile.
all:
	(cd misc; make all)
	(cd pipe; make all GUIMODE=$(GUIMODE) TKLIBS="$(TKLIBS)" TKINC="$(TKINC)")
	(cd seq; make all GUIMODE=$(GUIMODE) TKLIBS="$(TKLIBS)" TKINC="$(TKINC)")
	(cd y86-code; make all)

clean:
	rm -f *~ core
	(cd misc; make clean)
	(cd pipe; make clean)
	(cd seq; make clean)
	(cd y86-code; make clean)
	(cd ptest; make clean)

```

But I keep getting the following error...

```
psim.c:23:16: fatal error: tk.h: No such file or directory

```

I can't figure this out. Below is the whole output from terminal when I try to make the file. Thanks in advance for your help.

```
dan@DellLaptop:~/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim$ make clean; make
rm -f *~ core
(cd misc; make clean)
make[1]: Entering directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/misc'
rm -f *.o *.yo *.exe yis yas hcl2c mux4 *~ core.* 
rm -f hcl.tab.c hcl.tab.h lex.yy.c
make[1]: Leaving directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/misc'
(cd pipe; make clean)
make[1]: Entering directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/pipe'
rm -f psim pipe-*.c *.o *.exe *~ 
make[1]: Leaving directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/pipe'
(cd seq; make clean)
make[1]: Entering directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/seq'
rm -f ssim ssim+ seq*-*.c *.o *~ *.exe *.yo *.ys
make[1]: Leaving directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/seq'
(cd y86-code; make clean)
make[1]: Entering directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/y86-code'
rm -f *.o *.yis *~ *.yo *.pipe *.seq *.seq+ core
make[1]: Leaving directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/y86-code'
(cd ptest; make clean)
make[1]: Entering directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/ptest'
rm -f *.o *~ *.yo *.ys
make[1]: Leaving directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/ptest'
(cd misc; make all)
make[1]: Entering directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/misc'
gcc -Wall -O2 -c yis.c
gcc -Wall -O2 -c isa.c
isa.c: In function ‘load_mem’:
isa.c:204:10: warning: variable ‘hexcode’ set but not used [-Wunused-but-set-variable]
isa.c:203:9: warning: variable ‘addr’ set but not used [-Wunused-but-set-variable]
isa.c:202:9: warning: variable ‘empty_line’ set but not used [-Wunused-but-set-variable]
gcc -Wall -O2 yis.o isa.o -o yis
gcc -Wall -O2 -c yas.c
gcc -O2 -c yas-grammar.c
gcc -Wall -O2 yas-grammar.o yas.o isa.o -lfl -o yas
bison -d hcl.y
flex hcl.lex
gcc -O2 node.c lex.yy.c hcl.tab.c outgen.c -o hcl2c
node.c: In function ‘show_expr_helper’:
node.c:364:6: warning: format not a string literal and no format arguments [-Wformat-security]
node.c:371:6: warning: format not a string literal and no format arguments [-Wformat-security]
outgen.c: In function ‘print_token’:
outgen.c:40:3: warning: format not a string literal and no format arguments [-Wformat-security]
make[1]: Leaving directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/misc'
(cd pipe; make all GUIMODE=-DHAS_GUI TKLIBS="-L/usr/lib -ltk8.5 -ltcl8.5" TKINC="-isystem /usr/include/tcl8.5")
make[1]: Entering directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/pipe'
# Building the pipe-std.hcl version of PIPE
../misc/hcl2c -n pipe-std.hcl < pipe-std.hcl > pipe-std.c
gcc -Wall -O2 -isystem /usr/include/tcl8.5 -I../misc -DHAS_GUI -o psim psim.c pipe-std.c \
		../misc/isa.c -L/usr/lib -ltk8.5 -ltcl8.5 -lm
psim.c:23:16: fatal error: tk.h: No such file or directory
compilation terminated.
make[1]: *** [psim] Error 1
make[1]: Leaving directory `/home/dan/Documents/School Stuff/2012 I/CS 429/Labs/02 - Assembly/asmlab-handout/sim/pipe'
make: *** [all] Error 2

```

---

### Post by savanna on 2012-02-12
Do a search for the tk.h file - is it on your system??

eg

find / -type f -name tk.h

This line gives you a hint:

# Modify the following line so that gcc can find the tcl.h and **tk.h**

Is tk.h in /usr/include/tcl8.5 ?

---

### Post by Dan Again on 2012-02-12
Hi savanna,

Thanks for getting back to me. No, I was not able to find tk.h on my system...this was definitely the first thing I checked. I'm not sure what tk.h is, or how I'm supposed to get it on my system. I've downloaded Tcl and Tk and still no dice. I did numerous searches on Google to see what I could dig up and did not have any luck there either.

---

### Post by howefield on 2012-02-13
No school work assignments please.

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

Thread closed.

---

### Post by howefield on 2012-02-13
Thread re-opened.

---

### Post by Dan Again on 2012-02-13
Finally figured it out on my own, per the link below I needed to install tcl8.5-dev & tk8.5-dev.

[http://ubuntuforums.org/archive/index.php/t-1175019.html](http://ubuntuforums.org/archive/index.php/t-1175019.html)

---

