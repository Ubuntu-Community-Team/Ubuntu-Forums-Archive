---
title: "cannot execute binary file"
date: 2012-02-03
forum: General Help
---

### Post by conradin on 2012-02-03
Hi all I have an old Unix program that I cant see, to run on my modern linux box getting the error: ./atomtv: cannot execute binary file

Are there any tricks to getting a binary intended for Unix to run in linux?

---

### Post by imachavel on 2012-02-03
well if windows 7 is based on ms dos, then Linux is based on *nix, it's based on Unix kernel file system. I'm not too familiar with Unix, but it's sad to say so, because unix = linux with different gui, or perhaps it's head less. So I wouldn't know the answer to your question.

what is atom tv? how did it run on Unix? it gui based or command line based to execute? If it won't work on the binary, then it may not run at all. If it's more lower code level based to execute, maybe there is a way to fix it. If not, and it runs on higher level code, maybe there isn't a way to fix it. If the binary isn't recognised, it means the file isn't executing on the lowest level code possible to run. It just may not be supported.

---

### Post by sudodus on 2012-02-03
Linux programs can often be compiled from the source code to work in various computers. At least if there is not GUI. And for PCs the compiled code is portable, but with restrictions, for example 64-bit code cannot be run on a 32-bit cpu. PC code does not work on a power pc, but there is an ubuntu version for power pc.

An old program from Unix was probably compiled for a completely different kind of cpu, and in that case, it won't work in a PC.

---

### Post by Linux Dutchman on 2012-02-03
Maybe this helps: [https://sites.google.com/site/tipsandtricksforubuntu/executable-files](https://sites.google.com/site/tipsandtricksforubuntu/executable-files)

---

### Post by Khayyam on 2012-02-03
> **conradin said:**
> [...] Are there any tricks to getting a binary intended for Unix to run in linux?

It is unlikely. Even if it were compiled on a early Minix, Linux, or Redhat Linux 6 for that matter, then the versions of the libraries it linked to (glibc, libreadline, etc) would nolonger be avaialble on your system.

AIX, HP-AUX, Tru64, IRIX, Solaris, etc, have their own versions of libc, and many other libraries, so if its compiled on anything other than a GNU based system it is even less likely.

You might get some idea of the buildhost by running 'file atomtv', running 'strings atomtv | less' might also give you some useful information (runtime libraries, copyright info, --help, etc). If you have [gdb]("http://www.gnu.org/software/gdb/") installed that would no doubt spit out its reasons for exiting.

I wouldn't hold your breath .. nor place any wagers

HTH ..

---

### Post by dcstar on 2012-02-03
> **conradin said:**
> Hi all I have an old Unix program that I cant see, to run on my modern linux box getting the error: ./atomtv: cannot execute binary file

Are there any tricks to getting a binary intended for Unix to run in linux?

[LIST=1]
[*]Having the Execute bit set helps.
[*]If it is 32-bit and you are trying to run it on a 64-bit system, then you will need the appropriate libs.
[*]The post above this has the most likely issues.
[/LIST]

---

### Post by conradin on 2012-02-04
The original binary is for IRIX computers. I read that libygl could help these problems, but it even with the ygl library installed, the binary will not execute.

---

### Post by weblordpepe on 2012-02-04
conradin, we can use the **file** utility to tell us detailed information about the file.
can you please tell us the output of the following?```
file ././atomtv
```


Also, we can use **ptrace** to follow execution of a file. I'm not too sure if it'll work but worth giving it a shot (you may need to install ptrace)```
ptrace ./atomtv
```

For example I get this on some different files in my system:

```
**file /bin/ls**
/bin/ls: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```

```
**file /bin/busybox **
/bin/busybox: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, for GNU/Linux 2.6.15, stripped

```
```
file** ~/.wine/drive_c/windows/notepad.exe **
~/.wine/drive_c/windows/notepad.exe: PE32 executable for MS Windows (GUI) Intel 80386 32-bit

```

---

### Post by conradin on 2012-02-04
```
file atomtv
atomtv: ELF 32-bit MSB executable, MIPS, MIPS-I version 1 (SYSV), dynamically linked (uses shared libs), stripped

```

I dont have, not could I find ptrace. But I assume its like strace.
```
$ strace ./atomtv 
execve("./atomtv", ["./atomtv"], [/* 38 vars */]) = -1 ENOEXEC (Exec format error)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78d6000
_llseek(3, 0, 0xbfbaa228, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: Exec format error\n", 32strace: exec: Exec format error
) = 32
close(3)                                = 0
munmap(0xb78d6000, 4096)                = 0
exit_group(1)                           = ?

```

can mipps programs be made to work in ubuntu?

---

### Post by JonUK76 on 2012-02-05
I think it goes deeper than that, it's more a case of MIPS binaries are not going to be able to be run by your CPU, without some sort of emulator.  It's a completely different CPU from x86 processors, and not binary compatible.  Don't know if this is of some help as a starting point - [http://www.linux-mips.org/wiki/Emulators](http://www.linux-mips.org/wiki/Emulators)  I don't even know if this is possible, but if you could install SGI IRIX in an emulator that would probably be the best chance of getting the program working.

---

### Post by Khayyam on 2012-02-05
Conradin ..

This program is now nearly 20 years old (see the [release notes](http://www.bio.net/bionet/mm/xtal-log/1993-November/001393.html)), so, even if you were to have a SGI Graphics machine from that time period, and were able to run the program, you would be limited in only being able to output SGI RGB Images (.rgb) .. a somewhat outdated file format.
 
If you want to do some form of modeling then surely [PyMOL](http://www.pymol.org/) would be a better option. A package is not only available for Ubuntu, but it runs on *BSD, OS X, Windows, and probably many other OSes.

This is a case of find 'the right tool' .. visualisation software didn't cease to exist in the mid-ninties.

HTH ..

---

### Post by dcstar on 2012-02-06
> **JonUK76 said:**
> I think it goes deeper than that, it's more a case of MIPS binaries are not going to be able to be run by your CPU, without some sort of emulator. 
..........

Yep, if it was for something like SCO Unix that was x86 based then you may have had a chance, but not for something compiled for a totally foreign CPU architecture.

---

