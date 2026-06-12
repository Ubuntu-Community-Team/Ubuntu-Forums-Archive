---
title: "xmame can't find libGL.so, but it's there"
date: 2005-02-13
forum: General Help
---

### Post by linuxgrrl on 2005-02-13
when i try to run xmame, I get:
>GLmame v0.94 - the_peace_version , by Sven Goethel, >[http://www.jausoft.com](http://www.jausoft.com), [email]sgoethel@jausoft.com[/email],
>based upon GLmame v0.6 driver for xmame, written by >Mike Oliphant

>GLERROR: cannot access OpenGL library libGL.so
>GLERROR: dlerror() returns [libGL.so: cannot open >shared object file: No such file or directory]
>Segmentation fault
 
However, it appears to exist:

>mary@ubuntu:~ $ whereis libGL.so
>libGL: /usr/lib/libGL.so /usr/lib/libGL.a
>

what to do?

---

### Post by morebooks on 2005-02-13
Have you tried running "sudo ldconfig"? Not sure it will fix the problem, but its worth a shot.

---

### Post by linuxgrrl on 2005-02-13
[QUOTE=morebooks]Have you tried running "sudo ldconfig"? Not sure it will fix the problem, but its worth a shot.[/QUOTE]
 just tried it but still no success ... any other thoughts?

---

### Post by piedamaro on 2005-02-13
sudo ldconfig -v|grep GL

if it returns something like:
        libGL.so.1 -> libGL.so.1.0.6629
it should be ok. If not, add /usr/lib at the beginning of your /etc/ld.so.conf
 file then rerun ldconfig.

---

### Post by linuxgrrl on 2005-02-13
[QUOTE=piedamaro]sudo ldconfig -v|grep GL

if it returns something like:
        libGL.so.1 -> libGL.so.1.0.6629
it should be ok. If not, add /usr/lib at the beginning of your /etc/ld.so.conf
 file then rerun ldconfig.[/QUOTE]

running that command returns:
mary@ubuntu:~ $ sudo ldconfig -v|grep GL
Password:
        libGLU.so.1 -> libGLU.so.1.3
ldconfig: Cannot stat /usr/lib/libGL.so: No such file or directory
        libGLcore.so.1 -> libGLcore.so.1.0.6111
        libGLU.so.1 -> libGLU.so.1.3
        libGL.so.1 -> libGL.so.1.0.6111


I edited /etc/ld.so.conf as directed, and re-ran ldconfig, but still no success ...

---

### Post by piedamaro on 2005-02-14
You need to link /usr/lib/libGL.so to /usr/lib/libGL.so.1.0.6111

---

### Post by linuxgrrl on 2005-02-14
>>>You need to link /usr/lib/libGL.so to /usr/lib/libGL.so.1.0.6111

Thanks, that sounds promising! I'll try it when I get home.

I'm guessing the correct command is something like: 

$ sudo ln -s  /usr/lib/libGL.so /usr/lib/libGL.so.1.0.6111

---

### Post by piedamaro on 2005-02-14
[QUOTE=linuxgrrl]>>>You need to link /usr/lib/libGL.so to /usr/lib/libGL.so.1.0.6111

Thanks, that sounds promising! I'll try it when I get home.

I'm guessing the correct command is something like: 

$ sudo ln -s  /usr/lib/libGL.so /usr/lib/libGL.so.1.0.6111[/QUOTE]
 Nope :(
It's ln -s <target> <link name>:
sudo ln -s /usr/lib/libGL.so.1.0.6111 /usr/lib/libGL.so

---

### Post by linuxgrrl on 2005-02-15
[QUOTE=piedamaro]Nope :(
It's ln -s <target> <link name>:
sudo ln -s /usr/lib/libGL.so.1.0.6111 /usr/lib/libGL.so[/QUOTE]

Thank you! I figured that part out with trial and error last night ... and it works !

Fullscreen and everything.  Thank you thank you!!!!

---

### Post by piedamaro on 2005-02-16
[QUOTE=linuxgrrl]Thank you! I figured that part out with trial and error last night ... and it works !

Fullscreen and everything.  Thank you thank you!!!![/QUOTE]
 I'm glad it helped :)

---

