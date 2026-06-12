---
title: "gcc compilation error in festival"
date: 2010-05-31
forum: General Help
---

### Post by cneha on 2010-05-31
while compiling the following code

#include "/home/neha/Desktop/festival/src/include/festival.h"
int main(int argc,char **argv)
{
EST_Wave wave;
    int heap_size=210000;
    int load_init_files=1;
    festival_initialize(load_init_files,heap_size);
    //festival_say_file("/etc/motd");
    festival_eval_command("(voice_ked_diphone)");
    festival_say_text("hello world");
    festival_text_to_wave("hello world",wave);
    wave.save("/tmp/wave.wav","riff");
    festival_wait_for_spooler();
    return 0;
    }

**i am getting the error..**


**** Build of configuration Debug for project neha ****

make all 
Building target: neha
Invoking: GCC C++ Linker
g++ -L/usr/lib -o"neha"  ./src/neha.o   -llibeststring.a -llibestbase.a -llibestools.a -llibFestival.a
/usr/bin/ld: cannot find -llibeststring.a
collect2: ld returned 1 exit status
make: *** [neha] Error 1


Can anyone resolve the problem??

---

### Post by cneha on 2010-06-04
i solved this problem.
while linking the libraries for e.g. while linking the library libFestival.a,just use Festival instead of the libFestival.a..

---

### Post by gefthebest on 2011-10-18
Hi,

I am getting the same error:
/usr/bin/ld: cannot find -l/usr/lib/libFestival.a
collect2: ld returned 1 exit status

What did you do for the other libraries?
-leststring.a -lestbase.a -lestools.a
doesn't work...

Thanks

---

