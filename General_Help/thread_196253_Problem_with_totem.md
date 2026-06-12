---
title: "Problem with totem"
date: 2006-06-13
forum: General Help
---

### Post by IndigoMontoya on 2006-06-13
Every time I run totem I get a wierd message and it crashes any thoughts?

```
~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 69 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by yteh on 2006-06-14
Looks familiar. You might want to check out this previous post for a possible solution:
[http://ubuntuforums.org/showthread.php?t=185784&highlight=totem+crash](http://ubuntuforums.org/showthread.php?t=185784&highlight=totem+crash)

---

### Post by IndigoMontoya on 2006-06-14
thanks, Ill go look there

---

### Post by IndigoMontoya on 2006-06-14
I just rename /usr/share/totem/totem_logo.png to totem_logo.png.old and it worked fine.  Thanks for the direction!

I thought it would be MUCH more complicated then that

---

