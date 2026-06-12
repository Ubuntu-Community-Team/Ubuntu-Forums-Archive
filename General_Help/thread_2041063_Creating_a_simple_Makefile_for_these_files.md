---
title: "Creating a simple Makefile for these files"
date: 2012-08-11
forum: General Help
---

### Post by trilobite on 2012-08-11
Hi all.  
I've found source files for an old public-domain assembler, but it needs a Makefile. 

The C files are dasm.c , dasmdbg.c , dasmq.c . 

The header files are dasm.h , dprotos.h and runfile.h .  

I've struggled to put together a simple Makefile to get these files to compile, but with no luck. This is what I have so far - 
```
 

#  Makefile for DASM   

CC = gcc
CFLAGS = -O2 -Wall -g $(DEFINES)
INCPATH = -I.
LDFLAGS = $(SYSLDFLAGS) $(MYLDFLAGS)
LIBS = -l$(SYSLIBS) $(MYLIBS)
RM = rm -f 

srcdir = .  

SRCS  = *.C  

OBJS    = $(SRCS:.c=.o) 

$(OBJS): *.H  

.PHONY:  all 

all:	$(OBJS)
	$(CC) $(LDFLAGS) -o $@ $(OBJS) $(LIBS)


``` 

When I run Make on this, it gives me this -  
make: Nothing to be done for `DASM.C'.

So, is anyone able to help out and create a simple Makefile that should work? 
*Surely*, it can't be that hard, but when it comes to Make, it's all a mystery to me..... 
Many thanks in advance - 
- trilobite

---

### Post by kjohri on 2012-08-11
```
#  Makefile for DASM   

CC = gcc
CFLAGS = -O2 -Wall -g $(DEFINES)
INCPATH = -I.
LDFLAGS = $(SYSLDFLAGS) $(MYLDFLAGS)
LIBS = -l$(SYSLIBS) $(MYLIBS)
RM = rm -f 
HEADERS= dasm.h dprotos.h runfile.h 
OBJECTS = dasm.o dasmdbg.o dasmq.o
%.o: %.c
        $(CC) $(CFLAGS) $< -o $@

dasm: $(OBJECTS)
         $(CC) $(LDFLAGS) $(OBJECTS) -o $@ $(LIBS)

dasm.o: $(HEADERS)
dasmdbg.o: $(HEADERS)
dasmq.o: $(HEADERS)

.PHONY: clean
clean:
        rm *.o dasm
```

[http://www.softprayog.in/tutorials/make-primer]("http://www.softprayog.in/tutorials/make-primer")
[http://www.softprayog.in/tutorials/make-advanced]("http://www.softprayog.in/tutorials/make-advanced")

---

### Post by trilobite on 2012-08-11
> **kjohri said:**
> ```
#  Makefile for DASM   

CC = gcc
CFLAGS = -O2 -Wall -g $(DEFINES)
INCPATH = -I.
LDFLAGS = $(SYSLDFLAGS) $(MYLDFLAGS)
LIBS = -l$(SYSLIBS) $(MYLIBS)
RM = rm -f 
HEADERS= dasm.h dprotos.h runfile.h 
OBJECTS = dasm.o dasmdbg.o dasmq.o
%.o: %.c
        $(CC) $(CFLAGS) $< -o $@

dasm: $(OBJECTS)
         $(CC) $(LDFLAGS) $(OBJECTS) -o $@ $(LIBS)

dasm.o: $(HEADERS)
dasmdbg.o: $(HEADERS)
dasmq.o: $(HEADERS)

.PHONY: clean
clean:
        rm *.o dasm
```

[http://www.softprayog.in/tutorials/make-primer]("http://www.softprayog.in/tutorials/make-primer")
[http://www.softprayog.in/tutorials/make-advanced]("http://www.softprayog.in/tutorials/make-advanced")

Hi kjohri!  
  Awesome! Thanks very much for that, that's great! I'll give that a go. 

UPDATE: I've tried this now, but I get this message -  
make: *** No rule to make target `dasm.h', needed by `dasm.o'.  Stop.

UPDATE 2 - Fixed - it was me - DOH. The files have uppercase names - that's why they weren't found. I should be fine now.... 
Arrgh..... 

UPDATE 3 - YES!!! Everything is working perfectly now - thanks again, kjohri!  
- trilobite

---

