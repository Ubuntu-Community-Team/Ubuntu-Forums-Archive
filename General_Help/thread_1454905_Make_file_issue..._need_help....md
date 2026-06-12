---
title: "Make file issue... need help..."
date: 2010-04-15
forum: General Help
---

### Post by vikramtheone on 2010-04-15
Hi guys,
        may be makefile related questions are out of context here. Posting it because of lacking knowledge in it. Help!!!

I'm in trouble with the building process of simple C project with the Makefile. I'm new to the Makefile concept of building projects. I just made a small C project in Eclipse with  a directory structure as seen below.

                     [IMG]http://www.freeimagehosting.net/uploads/a53f98efea.jpg[/IMG]
	
**Project**

Here, the Makefile in the **maketest** directory has a loop which invokes the other three Makefiles.

**My problem**

The problem what I'm facing is that, after the makefiles send to the GCC the Fn1.c and Fn2.c files for compiling, the GCC will generate the respective object files (Fn1.o and Fn2.o). The third makefile(related to  main.c) will then send the **main.c** file for compiling to GCC, but at this time around when the GCC compiles the main.c (no errors shown - main() has only a printf) it is not generating the required **main.o** file and thats it, thats the problem. So, because of this when the **hello** part of the make file comes into execution the GCC is not able to find the required main.o to do its job and I get the following message there -

**gcc: main.o: No such file or directory**


Why is that the GCC is not able to create the **main.o** object file?

**Strange Observation worth mentioning**

Another strange observation worth mentioning here is that a file named **a.exe** is getting generated in the folder **main **and I don't understand how or why?

**[COLOR="Red"]I'm pasting all the necessary information below.[/COLOR]**

This project is just an exercise to me, I'm trying to learn from here to write makesfiles for a larger project. Kindly help.

Thanks

-V

**_________________________________________________________________**

I'm pasting here all the important parts of the **4 makefiles** and also the **error messages** I get on the console -

**1. Fn1/Makefile**

#Hardware platform details
HW = i486

#All Flags
# Compiler Flags
CCFLAGS = -mcpu=$(HW)


all: Fn1.o
	
Fn1.o: src/Fn1.c header/Fn1.h
	@echo ".compiling Fn1.c"
	$(CC) $(CCFLAGS) -Iheader -c src/Fn1.c
	
clean:
	@echo "cleaning up Fn1.o"
	rm -rf *o Fn1


**2. Fn2/Makefile**

#Hardware platform details
HW = i486 

#All Flags
# Compiler Flags
CCFLAGS = -mcpu=$(HW)

all: Fn2.o

Fn2.o: src/Fn2.c header/Fn2.h
	@echo ".compiling Fn2.c"
	$(CC) $(CCFLAGS) -Iheader -c src/Fn2.c

clean:
	@echo ".cleaning up Fn2.o"
	rm -rf *o Fn2 

**3. main/Makefile**

#Hardware platform details
HW = i486 

#All Flags
# Compiler Flags
CCFLAGS = -mcpu=$(HW)

#OBJECTS
OBJ = ../Fn1/Fn1.o ../Fn2/Fn2.o main.o

all: hello
	
hello: $(OBJ)
	@echo "making hello"
	$(CC) -o $@ $(OBJ)
	
main.o: main.c ../Fn1/header/Fn1.h ../Fn2/header/Fn2.h
	@ echo ".compiling main.c"
	$(CC) $(CCFLAGS) -I../Fn1/header -I../Fn2/header main.c

clean:
	@echo "cleaning up"
	rm -rf *o hello	

**4. root/Makefile**

#Modules
MODULES = Fn1 Fn2 main

all:
	for dir in $(MODULES); do \
		(cd $$dir; ${MAKE} all); \
	done
   

**5. Messages I receive when I build the project**

make[1]: Entering directory `/cygdrive/c/Vikram/Projects/maketest/Fn1'

make[1]: `all' is up to date.

make[1]: Leaving directory `/cygdrive/c/Vikram/Projects/maketest/Fn1'

make[1]: Entering directory `/cygdrive/c/Vikram/Projects/maketest/Fn2'

make[1]: Nothing to be done for `all'.

make[1]: Leaving directory `/cygdrive/c/Vikram/Projects/maketest/Fn2'

make[1]: Entering directory `/cygdrive/c/Vikram/Projects/maketest/main'

.compiling main.c

C:/cygwin/bin/gcc -mcpu=i486  -I../Fn1/header -I../Fn2/header main.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.

making hello

C:/cygwin/bin/gcc -o hello ../Fn1/Fn1.o ../Fn2/Fn2.o main.o

gcc: main.o: No such file or directory

make[1]: *** [hello] Error 1

make[1]: Leaving directory `/cygdrive/c/Vikram/Projects/maketest/main'

make: *** [all] Error 2

---

