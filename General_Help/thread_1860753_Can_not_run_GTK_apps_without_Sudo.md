---
title: "Can not run GTK apps without Sudo"
date: 2011-10-15
forum: General Help
---

### Post by 8_Bit on 2011-10-15
I'm trying to run Banshee in Kubuntu 11.10.

When I run it in the command line I get the following error:

> [Info  00:05:57.991] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, x86_64) @ 2011-09-23 04:47:58 UTC]
The program 'Banshee' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAccess (attempt to access private resource denied)'.
  (Details: serial 549 error_code 10 request_code 158 minor_code 1)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


If I try running it as root (using *sudo) *it actually starts.

Does anyone have a clue what could be causing this?

Reinstalling it did not help.

Thanks in advance.

---

