---
title: "Installing ppmtomd for ALPS printer"
date: 2009-09-04
forum: General Help
---

### Post by carolineL on 2009-09-04
I am trying to use Jaunty with an old ALPS2300. I have got the ALPS printing test pages using the old MD2k driver but wanted to use ppmtomd for its additional features (metallic inks). Although the Add Printer dialog suggests ppmtomd as recommended, this appears just to be the text from the .ppd file, as when I attempt to print, I get the following error lines (rest snipped):
D [03/Sep/2009:12:18:37 +0100] [Job 5]',
'D [03/Sep/2009:12:18:37 +0100] [Job 5] Starting process "renderer" (generation 2)',
'D [03/Sep/2009:12:18:37 +0100] [Job 5] /bin/bash: ppmtomd: command not found',
'D [03/Sep/2009:12:18:38 +0100] [Job 5] GPL Ghostscript 8.64: Unrecoverable error, exit code 1',
'D [03/Sep/2009:12:18:38 +0100] [Job 5] renderer exited with status 127',
'D [03/Sep/2009:12:18:38 +0100] [Job 5] Kid3 exit status: 1',
'E [03/Sep/2009:12:18:38 +0100] PID 4422 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!',
It appears the actual ppmtomd exe is nowhere on my hard drive, though the .ppd is.  My (probably faulty) understanding is that ppmtomd.exe runs at some stage after ghostscript as a separate program to convert/filter the file to the correct format, as compared with earlier drivers such as MD2k which somehow integrate more directly with Ghostscript.
I could find no download of the exe, so attempted to 'make install' the ppmtomd c source files. Eventually got a compilation but link fails because it is looking for libppm.a and others which appear no longer to exist (libnetpbm different structure?)
 
Can someone please help me find an exe that I can actually use (32 bit) - I assume I just add it to the usr/lib/CUPS folder and it gets scripted to run? (Oh I also tried to get it out of a Mandrake rpm using alien, but I even managed to kill an alien, so that got nowhere.)
Or perhaps gently correct my mistaken understanding? Other people on this and other forums have apparently successfully included their printers simply by getting the right .ppd file - which as far as I can see is just a list of fields. Presumably their actual drivers are already in the distro?
Thanks for any help...

---

### Post by carolineL on 2009-09-04
Ok, solved it myself! But I think something needs doing (maybe at Open printing database?) so solution is available for others.
Solution:

[LIST]
[*]Download ppmtomd-1.5 tar (all source files and make file).
[*]Ensure libnetpdm and libnetpdm-dev available - the latter provides the header files #included by ppmtomd.c.
[*]Change ppmtomd make file so that linker line read as follows:
[/LIST]
[INDENT]$(CC) -o ppmtomd $(OBJS) $(LDLIBS) -lnetpbm -lm

[/INDENT][INDENT](ie remove references to deprecated libraries and replace by netpbm)
[/INDENT]
[LIST]
[*]Run make install, and check that ppmtomd executable is generated (don't worry about the fact that it complains about where to put the MAN file - I haven't worked that out yet)
[*]Move the ppmtomd executable from the folder where you built it to usr/lib/CUPS/filter
[*]Install the printer using the Add Printer dialog, specifying the .ppd file to pick up (this assumes you have got the .ppd file from the Open Printing database ready)
[/LIST]
The .c files for ppmtomd seem to be dependent on headers and libraries that were updated in 2002/3 when netpbm changed. I guess older distributions still supplied versions for back-compatibility. 
If the #include lines in the code are updated to #include pam.h instead (if the other headers ever disappear) then other changes will be required to the code to use the new functions

---

### Post by keithwwalker on 2011-05-01
Thanks for the tips, I have an old MD1000 in great shape and it would be wonderful to get it running with Ubuntu!

Quick question, does the ppmtomd printing interface similar to the windows version (with options for overlay, dpi, foils etc?  Or is this just a basic print driver?

More detailed question: When you refer to libnetp**_d_**m and libnetp**_d_**m-dev is that a typo or are you refering to libnetp**_b_**m and libnetp**_b_**m-dev?

Thanks
Keith Walker

---

### Post by keithwwalker on 2011-05-01
I got it to print a test page!
Apparently you were talking about libnetp**_b_**m and libnetp**_b_**m-dev.

Here's the noobs guide to what I did.  Let me know if I did anything wrong.

I still can't see how to do spot color with foils???

I extracted the ppmtomd-1.6.tar.gz file
Then in terminal:
```

keithwwalker@keithwwalker-desktop:~$ cd /home/keithwwalker/Desktop/ppmtomd-1.6
keithwwalker@keithwwalker-desktop:~/Desktop/ppmtomd-1.6$ make
gcc -O2  -W -Wall -Wstrict-prototypes -c ppmtomd.c 
ppmtomd.c: In function ‘main’:
ppmtomd.c:2204: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2204: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2224: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2224: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2229: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2229: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2234: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2234: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2240: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2240: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2244: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2244: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2264: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2264: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2284: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2284: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2313: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2313: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2326: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2326: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2334: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2334: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2337: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2337: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2340: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2340: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2344: warning: pointer targets in passing argument 2 of ‘page_info.out_function’ differ in signedness
ppmtomd.c:2344: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2126: warning: ignoring return value of ‘mkstemp’, declared with attribute warn_unused_result
ppmtomd.c:2287: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
ppmtomd.c: In function ‘rgl_init_page’:
ppmtomd.c:2488: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2488: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2490: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2490: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2495: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2495: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2497: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2497: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2501: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2501: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2506: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2506: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2511: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2511: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2516: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2516: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2522: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2522: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2543: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2543: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2550: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2550: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2554: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2554: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:2561: warning: pointer targets in passing argument 2 of ‘page_info->out_function’ differ in signedness
ppmtomd.c:2561: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c: In function ‘print_page’:
ppmtomd.c:3241: warning: pointer targets in passing argument 2 of ‘prn_out’ differ in signedness
ppmtomd.c:3241: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ppmtomd.c:3269: warning: pointer targets in passing argument 1 of ‘packbits’ differ in signedness
ppmtomd.c:2362: note: expected ‘char *’ but argument is of type ‘unsigned char *’
ppmtomd.c:3269: warning: pointer targets in passing argument 3 of ‘packbits’ differ in signedness
ppmtomd.c:2362: note: expected ‘char *’ but argument is of type ‘unsigned char *’
ppmtomd.c:3269: warning: pointer targets in passing argument 4 of ‘packbits’ differ in signedness
ppmtomd.c:2362: note: expected ‘char *’ but argument is of type ‘unsigned char *’
ppmtomd.c:3306: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
/usr/include/bits/stdio2.h:32: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
ppmtomd.c:3313: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
/usr/include/bits/stdio2.h:32: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
ppmtomd.c:3320: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
/usr/include/bits/stdio2.h:32: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
ppmtomd.c:3327: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
/usr/include/bits/stdio2.h:32: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
ppmtomd.c:3335: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
/usr/include/bits/stdio2.h:32: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
ppmtomd.c:3352: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
/usr/include/bits/stdio2.h:32: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
gcc    -c -o mddata.o mddata.c
gcc    -c -o photocolcor.o photocolcor.c
gcc    -c -o vphotocolcor.o vphotocolcor.c
gcc    -c -o dyesubcolcor.o dyesubcolcor.c
gcc -o ppmtomd ppmtomd.o mddata.o photocolcor.o vphotocolcor.o dyesubcolcor.o  -lnetpbm -lm
keithwwalker@keithwwalker-desktop:~/Desktop/ppmtomd-1.6$ 

```

Then

```
keithwwalker@keithwwalker-desktop:~$ gksudo nautilus

```

To graphically copy the 
```
ppmtomd
``` 
file into the 
```
/usr/lib/cups/filter
```
file folder.

Then installed printer with the ppd saved on my desktop:
[Alps MD 1000 Driver]("http://www.openprinting.org/ppd-o-matic.php?driver=ppmtomd&printer=Alps-MD-1000&show=0")

Keith Walker

> **keithwwalker said:**
> Thanks for the tips, I have an old MD1000 in great shape and it would be wonderful to get it running with Ubuntu!

Quick question, does the ppmtomd printing interface similar to the windows version (with options for overlay, dpi, foils etc?  Or is this just a basic print driver?

More detailed question: When you refer to libnetp**_d_**m and libnetp**_d_**m-dev is that a typo or are you refering to libnetp**_b_**m and libnetp**_b_**m-dev?

Thanks
Keith Walker

---

