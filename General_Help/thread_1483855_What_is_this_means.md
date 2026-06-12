---
title: "What is this means??"
date: 2010-05-15
forum: General Help
---

### Post by jungwook on 2010-05-15
I faced with a problem. The program didn't run and the massage appeared 

> 
Segmentation fault (SIGSEGV) in main thread
.....
xxxx.so
So, I used ldd command.

ldd xxxx.so

> 
libvtutils.so => not found
    libpthread.so.0 => /lib/libpthread.so.0 (0x00007fdd5391e000)
    libelf.so.1 => /usr/lib/libelf.so.1 (0x00007fdd53709000)
    libdl.so.2 => /lib/libdl.so.2 (0x00007fdd53505000)
    libbz2.so.1 => /lib/libbz2.so.1 (0x00007fdd532f4000)
    libz.so.1 => /lib/libz.so.1 (0x00007fdd530db000)

My question is what the number??
> /lib/libpthread.so.0 ( [COLOR=Red]0x00007fdd5391e000[/COLOR] )I mean I wander the meaning of the numbers.

Thank you.

---

### Post by BoneKracker on 2010-05-15
I believe this hexadecimal number is the memory address where the object would be loaded.

Notice that the number changes (the address is determined dynamically).  See what happens when you run the command twice:
```
typhoon lib # ldd libiw.so.29 
	linux-gate.so.1 =>  (0xb77aa000)
	libm.so.6 => /lib/libm.so.6 (0xb776e000)
	libc.so.6 => /lib/libc.so.6 (0xb7629000)
	/lib/ld-linux.so.2 (0xb77ab000)
typhoon lib # ldd libiw.so.29 
	linux-gate.so.1 =>  (0xb77ab000)
	libm.so.6 => /lib/libm.so.6 (0xb776f000)
	libc.so.6 => /lib/libc.so.6 (0xb762a000)
	/lib/ld-linux.so.2 (0xb77ac000)
```

This number varies depending on the order in which objects are loaded into memory.  On a securely configured system, the addresses where objects are loaded are intentionally randomized.

Your problem seems to be that libvtutils.so is missing.  The library itself may not have been installed, or the symlink "libvtutils.so" may be missing or pointing to nothing.

---

### Post by jungwook on 2010-05-15
Ok! Thank you so much.

My sistem is amd64.

So, the address number is 64bit.

Yes, I tried to run ldd twice and I realized the number is change.

Now, I clearly understood and thank you so much.^^

---

