---
title: "problem displaying Solaris remote X11 on Ubuntu"
date: 2009-07-06
forum: General Help
---

### Post by gdommett on 2009-07-06
hello, I'm not quite sure if this is the right place to post this.

I have a Ubuntu 8.10 laptop for some reason, when I ssh -X to a solaris 10 box from it, and try to run an X application, I get the error message at the end of this post. It does not matter what the application is, the error is always the same

ssh -X to the same solaris 10 box does work from a Debain linux machine, and from windows using putty + xming.

In addition, ssh -X from the ubuntu laptop to the fore mentioned Debian linux machine does work without problem.

Does anyone have any idea what on earth is causing this ?

Password: 
Last login: Mon Jul  6 08:28:13 2009 from geoffrey-web.lan
Sun Microsystems Inc.   SunOS 5.10      Generic January 2005
$ gedit
The program 'gedit' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 11 error_code 3 request_code 154 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
$

---

