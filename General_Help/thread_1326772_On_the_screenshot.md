---
title: "On the screenshot"
date: 2009-11-14
forum: General Help
---

### Post by ygao on 2009-11-14
[SIZE=4]Hi all,

I want to take a screen shot of a certain window. So I tried to use the "Grab the current window" option in "take screenshot" application. However, after I hit "take screenshot", nothing happened. Usually, a dialog window would pop up to ask where to save the png picture. Anyone knows why?

Thanks.
ygao
[/SIZE]

---

### Post by Tiganjero on 2009-11-14
I think that it would be easier to just press the Print Screen button :)

Cheers,
George

---

### Post by sisco311 on 2009-11-14
> **ygao said:**
> Hi all,

I want to take a screen shot of a certain window. So I tried to use the "Grab the current window" option in "take screenshot" application. However, after I hit "take screenshot", nothing happened. Usually, a dialog window would pop up to ask where to save the png picture. Anyone knows why?

Thanks.
ygao


Hi,

I can reproduce the same behavior.

If I run:
```
gnome-screenshot --interactive
```
in a terminal and select the *Grab the current window* then press *Take Screenshot* a get this error message:
```
The program 'gnome-screenshot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 1424 error_code 3 request_code 15 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

To fix it set the *Grab after a delay of* counter to non-zero.


EDIT: 
Please don't use big fonts. Thanks.

---

