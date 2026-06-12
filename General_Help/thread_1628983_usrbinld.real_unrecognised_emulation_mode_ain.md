---
title: "/usr/bin/ld.real: unrecognised emulation mode: ain"
date: 2010-11-23
forum: General Help
---

### Post by Nikolazigic on 2010-11-23
I have a problem with this:
/usr/bin/ld.real: unrecognised emulation mode: ain
Supported emulations: elf_x86_64 elf_i386 i386linux
collect2: ld returned 1 exit status
My comp is x86_64 what should I do?

---

### Post by Nikolazigic on 2010-11-23
I think that I have to put something in my makefile:
FFLAGS =  -O4 -g 
#CFLAGS =  -O -I/usr/openwin/include
CFLAGS =  -O 
LDFLAGS= -L/usr/lib/libf2c.a -m64


#
#rules for compiling .f files:
#
.f.o:
    $(COMPILE.f) $(FFLAGS) $< $(INCS)
.c.o:
    $(COMPILE.c) $(CFLAGS) $< $(INCS)
#---------------------------------------------------------------------------
#
# Source objects
#
MT2DDI_OBJS=  driver.o solve_mt2d_direct.o boem.o rotz.o gebolr.o d2emod.o pobo.o mte.o d2hmod.o gsres.o mth.o z1idu.o h1iud.o phase.o
#
# Executable name
#
MT2DDI_EXEC=$(EXEDIR)/mt2ddi
#
mt2ddi: $(MT2DDI_EXEC)
$(MT2DDI_EXEC): ${MT2DDI_OBJS}
    f77 -o -m64${MT2DDI_OBJS}
    mv main ${MT2DDI_EXEC}

---

### Post by Nikolazigic on 2010-11-23
May be iti is somehow related to lib 64 issue?

---

### Post by Nikolazigic on 2010-11-24
**Re: unrecognised emulation mode: elf_x86_64**

 			OliveAddict
			Thu, 24 Mar 2005 14:35:23 -0800
 		
        FYI, it turns out that for some odd reason, the system had a 32-bit ld
installed.  I took the 64-bit binutils RPM from the RHEL3 U3 media and
forced installation of the package.  With a 64-bit linker, my problem
was solved.
Does anyone have links to Debian 64bit repsoitories?

---

