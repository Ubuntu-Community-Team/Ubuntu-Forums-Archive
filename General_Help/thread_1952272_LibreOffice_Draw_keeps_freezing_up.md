---
title: "LibreOffice Draw keeps freezing up"
date: 2012-04-04
forum: General Help
---

### Post by MarjaE on 2012-04-04
I'm currently using LibreOffice Draw .34 on Ubuntu 11.04 in Gnome 2/Classic for several projects.

Unfortunately, LibreOffice Draw has been peculiarly slow and prone to freezing. It takes forever, and several attempts, to reposition objects because LibreOffice keeps freezing. If working or saving, CPU usage often exceeds 100% and I've seen as high as 122%. I've tried quitting LibreOffice and restarting it, without success.

---

### Post by TeoBigusGeekus on 2012-04-06
Any error messages when you run it from terminal?

---

### Post by arjmage on 2012-07-10
I am having the same error with libreoffice. Writer in this case, but I think the basic program that runs is soffice.bin. The document is manuscript with about 20 pages, and 5 or 6 figures and a table plus several citation references. The freezing problem seems to be occurring after inserting the figures and references.

I ran it from the terminal. Here is the message:


The program 'soffice' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 53972 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

OS: Ubuntu 10.04
Libreoffice: 3.5.4.2

What could be the error?

---

