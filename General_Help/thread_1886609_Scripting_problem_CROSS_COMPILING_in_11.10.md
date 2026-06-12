---
title: "Scripting problem CROSS_COMPILING in 11.10"
date: 2011-11-25
forum: General Help
---

### Post by eaanon01 on 2011-11-25
Hi
 
First post here.
I have a problem with running a scpt taking care of cross compiling in ubuntu. The script worked fine on older versions. I now have 11.10
 
One of the lines state:
 
make ARCH=avr32 CROSS_COMPILE=avr32-linux-
and the result:
make: avr32-linux-gcc: Command not found
 
while avr32-linux-gcc is available by my PATH setting:
 
avr32-linux-addr2line avr32-linux-c++filt avr32-linux-gccbug avr32-linux-ldconfig avr32-linux-ranlib
avr32-linux-ar avr32-linux-cpp avr32-linux-gcov avr32-linux-ldd avr32-linux-readelf
avr32-linux-as avr32-linux-g++ avr32-linux-gdb avr32-linux-nm avr32-linux-size
avr32-linux-c++ [COLOR=red]avr32-linux-gcc[/COLOR] avr32-linux-gprof avr32-linux-objcopy avr32-linux-strings
avr32-linux-cc avr32-linux-gcc-4.2.4 avr32-linux-ld avr32-linux-objdump avr32-linux-strip
user@ubuntu1010desktop:~/Desktop$ avr32-linux-
 
Does anyone know any reason for why this is not working. I can go to the folder and paste in the same command and it runs perfectly.

---

