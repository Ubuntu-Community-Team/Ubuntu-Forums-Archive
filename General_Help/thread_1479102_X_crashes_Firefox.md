---
title: "X crashes Firefox"
date: 2010-05-10
forum: General Help
---

### Post by Mainlake on 2010-05-10
Hi all!

I have problem with Firefox 3.6.3 randomly crashing assumingly with "help" of X server. This crash doesn't happen immediately after starting, but after a random amount of time. And I've been unable to trace down the reason for this crash.
Below is the commandline information:

```
@experience:~$ firefox 
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 4857623 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
@experience:~$ firefox --sync
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 32008423 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault
```

Do you have any ideas?

---

### Post by viralmeme on 2010-05-10
Google ... Last post: 30 Oct 2008 ... looks like they reintroduced a bug from 2008 .. :(

Results **1** - **10** of about **2,930** for **"The program  'firefox-bin' received an X Window System error"**.

---

### Post by Mainlake on 2010-05-10
Hmm, changed GTK+ Style to "Raleigh" in System settings and it seems to work. So this is a bug in QtCurve, or?

Ps. It looks ugly :P

---

### Post by Mainlake on 2010-05-11
Now I've tested with the "Raleigh" and the symptoms are almost the same, I only get more information to console, i.e. BadPixmap.

```
@experience:~$ firefox --sync
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 3331759 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 3331760 error_code 4 request_code 54 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Now I'll try with different font, Serif instead of Sans Serif.

---

### Post by Mainlake on 2010-05-12
Anyone having any ideas?
This is getting a bit annoying :mad:

I will try without the desktop effects, and see if it helps.

---

### Post by Mainlake on 2010-05-18
Still experiencing same problems, help anyone?

---

