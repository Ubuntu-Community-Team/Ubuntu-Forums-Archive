---
title: "Gxine doesn't like full screen"
date: 2006-03-24
forum: General Help
---

### Post by Zalbor on 2006-03-24
If I try to make gxine go fullscreen, it crashes. It used to work fine at first. I tried a "complete removal" and installing it again afterwards, but it didn't get fixed. With normal xine, this doesn't happen.
Running it from a terminal, I get this:
```
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 152 error_code 8 request_code 42 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

I tried running gxine --sync (although I'm not one of its developers) but the exact same thing happened. Any ideas?

---

### Post by Zalbor on 2006-04-02
I noticed that this only happens when I load the 686-smp kernel. With the simple 686 one, it works. Is it possible to fix this?

---

