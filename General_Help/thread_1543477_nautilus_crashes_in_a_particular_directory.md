---
title: "nautilus crashes in a particular directory"
date: 2010-08-01
forum: General Help
---

### Post by kadil on 2010-08-01
I get this error from /var/log/messages:


[20837.671639] nautilus[3125]: segfault at 0 ip 010f524b sp b5cbbc0c error 4 in libc-2.11.1.so[fdd000+153000]

mc can browse there and copy files, delete files, etc

The directory is in a 1T external usb hard disk with ntfs filesystem. any ideas?

---

### Post by 5BallJuggler on 2010-08-04
Did you manage to fix it? I have the same fault accessing my home folder

```
Aug  4 20:47:47 phil-laptop kernel: [  560.369904] nautilus[1821]: segfault at bf0efffc ip 0049bf1c sp bf0f0000 error 6 in libgthread-2.0.so.0.2400.1[49a000+4000]
Aug  4 20:48:11 phil-laptop kernel: [  585.141596] nautilus[2126]: segfault at bf090fec ip 00e240ac sp bf090ff0 error 6 in libgobject-2.0.so.0.2400.1[df8000+3d000]
Aug  4 20:48:45 phil-laptop kernel: [  618.298251] nautilus[2146]: segfault at bf192ffc ip 00160f1c sp bf193000 error 6 in libgthread-2.0.so.0.2400.1[15f000+4000]
Aug  4 20:49:10 phil-laptop kernel: [  643.712236] nautilus[2187]: segfault at beed0fec ip 00719bcf sp beed0ff0 error 6 in libglib-2.0.so.0.2400.1[6c0000+c8000]
Aug  4 20:49:30 phil-laptop kernel: [  663.406703] nautilus[2207]: segfault at bf1edfac ip 002210ac sp bf1edfb0 error 6 in libgobject-2.0.so.0.2400.1[1f5000+3d000]
```

---

### Post by 5BallJuggler on 2010-08-04
> **5BallJuggler said:**
> Did you manage to fix it? I have the same fault accessing my home folder

```
Aug  4 20:47:47 phil-laptop kernel: [  560.369904] nautilus[1821]: segfault at bf0efffc ip 0049bf1c sp bf0f0000 error 6 in libgthread-2.0.so.0.2400.1[49a000+4000]
Aug  4 20:48:11 phil-laptop kernel: [  585.141596] nautilus[2126]: segfault at bf090fec ip 00e240ac sp bf090ff0 error 6 in libgobject-2.0.so.0.2400.1[df8000+3d000]
Aug  4 20:48:45 phil-laptop kernel: [  618.298251] nautilus[2146]: segfault at bf192ffc ip 00160f1c sp bf193000 error 6 in libgthread-2.0.so.0.2400.1[15f000+4000]
Aug  4 20:49:10 phil-laptop kernel: [  643.712236] nautilus[2187]: segfault at beed0fec ip 00719bcf sp beed0ff0 error 6 in libglib-2.0.so.0.2400.1[6c0000+c8000]
Aug  4 20:49:30 phil-laptop kernel: [  663.406703] nautilus[2207]: segfault at bf1edfac ip 002210ac sp bf1edfb0 error 6 in libgobject-2.0.so.0.2400.1[1f5000+3d000]
```

For anyone interested I downloaded "Thunar" file manager, it doesn't crash

---

