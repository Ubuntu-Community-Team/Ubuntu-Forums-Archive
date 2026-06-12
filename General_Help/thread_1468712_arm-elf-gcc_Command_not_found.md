---
title: "arm-elf-gcc: Command not found"
date: 2010-05-01
forum: General Help
---

### Post by michaelvh on 2010-05-01
hi everyone,

I'm trying to compile using a makefile with arm-elf-gcc on ubuntu 9.10. The problem is that I can't change the default path.  The error I get is 

```
michael@michael-laptop:~/Documents/usb_eth/src$ make
/disk2/tools/gnuarm/bin/arm-elf-gcc -c -I. -x assembler-with-cpp -mcpu=arm7tdmi   startup.S -o startup.o
make: /disk2/tools/gnuarm/bin/arm-elf-gcc: Command not found
make: *** [startup.o] Error 127

```the makefile is located at 'michael/Documents/usb_eth/src' and arm-elf-gcc at 'michael/toolchain/gnu-arm-installer/install/bin'. (michael is the home directory)

So it looks for arm-elf-gcc at the wrong location.

I followed the instructions from [http://ubuntuforums.org/showthread.php?t=748593](http://ubuntuforums.org/showthread.php?t=748593) (I added the line 'export PATH=$PATH:/toolchain/gnu-arm-installer/install/bin' to .bashrc and the line 'source $HOME/.bashrc' to .bash_profile, both in the home directory) and the path does seem to be changed, cause 'echo $PATH' returns
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:**/toolchain/gnu-arm-installer/install/bin**
```Still I get the same error.

Can anyone help?


thanks in advance,

Michael

---

### Post by jobix on 2010-05-01
> make: /disk2/tools/gnuarm/bin/arm-elf-gcc: Command not found

It doesn't seem to be looking in your /toolchain/gnu-.... directory but instead in the /disk2 directory. Check your Makefile to see where it's getting that "/disk2/tools..." from.

---

### Post by michaelvh on 2010-05-01
that's the weird thing, the makefile doesn't mention anything about that disk2/.. directory. :s

---

### Post by jobix on 2010-05-01
Try this while you are in that directory where the Makefile is:
> grep -i disk2 *

---

### Post by michaelvh on 2010-05-01
thank you very much!

the path was specified in another file in that directory, changing it solved my problem!

---

