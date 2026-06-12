---
title: "Segmentation Fault"
date: 2006-02-13
forum: General Help
---

### Post by spector on 2006-02-13
spector@fix_sid:~$ glxgears
Segmentation fault
spector@fix_sid:~$ mplayer
Segmentation fault
spector@fix_sid:~$ vlc
VLC media player 0.8.4 Janus
Segmentation fault


How is it possible?

What can i do?

Thanks..

---

### Post by heimo on 2006-02-13
Any background information? How did it start, is it a fresh install, did something change recently? Is packages configured properly:
```
sudo dpkg --configure -a
```

Seems a bit serious.

---

### Post by spector on 2006-02-13
I had some problems with the nvidia driver, so i recompiled the kernel.

Now i think that the driver work properly even if glxinfo gives back seg. fault.

I tried to rienstall VLC but i have the same problem...

---

### Post by heimo on 2006-02-13
So it's probably something about the new kernel, but I have no idea what it could be. Maybe you could take the configuration file from /boot/ directory for your old (Ubuntu stock) kernel (copy it to /usr/src/linux/.config), do only the neccessary changes (make menuconfig) and recompile once again.

:-k What are the changes you made to the kernel?

---

### Post by spector on 2006-02-13
I forgot to tell a important thing....

I had this problem also before the kernel recompiling, so i think that the proble do not stay in the kernel but in something else....

---

### Post by heimo on 2006-02-13
[quote=spector]I forgot to tell a important thing....

I had this problem also before the kernel recompiling, so i think that the proble do not stay in the kernel but in something else....[/quote] 
Ok. Then... I have no idea. I'd probably run something like
```
strace glxgears 2>trace
``` and examine the *trace *file for any causes for the sudden death.

---

### Post by spector on 2006-02-14
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXau.so.6", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\t\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=7052, ...}) = 0
old_mmap(NULL, 9996, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x3735f000
old_mmap(0x37361000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x37361000
close(3)                                = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x3735e000
mprotect(0x37452000, 4096, PROT_READ|PROT_WRITE) = 0
mprotect(0x37452000, 4096, PROT_READ|PROT_EXEC) = 0
mprotect(0x37454000, 7892992, PROT_READ|PROT_WRITE) = 0
mprotect(0x37454000, 7892992, PROT_READ|PROT_EXEC) = 0
mprotect(0x37ef3000, 430080, PROT_READ|PROT_WRITE) = 0
mprotect(0x37ef3000, 430080, PROT_READ|PROT_EXEC) = 0
set_thread_area({entry_number:-1 -> 6, base_addr:0x3735e8e0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
munmap(0x37f76000, 69088)               = 0
brk(0)                                  = 0x804d000
brk(0x806e000)                          = 0x806e000
open("/dev/zero", O_RDWR)               = 3
mmap2(NULL, 8192, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x37f85000
close(3)                                = 0
getpid()                                = 6260
mmap2(NULL, 380928, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x37301000
modify_ldt(17, {entry_number:666, base_addr:0x804d310, limit:512, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:0, seg_not_present:0, useable:1}, 16) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++


These are the last line of trace with glxgears


If i made strace with bzflag (that goes on seg. fault) i find this line

access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)


The same of glxgears....

And also the error is the same


mmap2(NULL, 380928, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x36f79000
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++


SO?

thnkx

---

### Post by spector on 2006-02-14
[http://saintaardvarkthecarpeted.com/blog/?p=182](http://saintaardvarkthecarpeted.com/blog/?p=182)


This was the solution.


TUCH and TRACE I love you!!!!

But now i havo problem with the sound... =)

With linux you have always somethign to do, i love it....


SPector

---

### Post by heimo on 2006-02-14
```
touch /etc/ld.so.nohwcap
``` solved it? =D> Excellent.

---

### Post by oofnik on 2006-04-18
Wow.. that was an.. interesting fix. Are there any side effects of this file? Why does it work? Why don't those programmer people document things like this?! Oh well I can listen to music again on my new kernel, thanks for finding the fix spector! :D
Now on to problem #1389...

---

