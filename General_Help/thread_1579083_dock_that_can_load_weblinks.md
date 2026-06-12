---
title: "dock that can load weblinks"
date: 2010-09-21
forum: General Help
---

### Post by Jonny5isalivetm on 2010-09-21
Hi all new user, trying dump ms haha 

I have few issues, in vista I used a dock called Rocket dock, I could load my favourite websites from the dock. How can I do this in Ubuntu?

Few other minor things..

a radio widget/gadget that works ?

my bank website only works correctly via IE, ive tried ies4linux but it says it only works on latest version of WINE 0.9.x even tho I have newer version installed..

Jonny

---

### Post by hariks0 on 2010-09-21
Hi, Welcome to Ubuntu,

Try [cairo dock]("http://glx-dock.org"):guitar:

---

### Post by Jonny5isalivetm on 2010-09-21
Hi been trying it actually, but it wont work properly with hyper links :(

thanks for the reply and friendly welcome :D

about IE if anybody can make heads or tales of this....

j5@j5-desktop:~$ '/home/j5/Desktop/ies4linux-2.99.0/ies4linux' 
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

The program 'ies4linux-gtk.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadGC (invalid GC parameter)'.
  (Details: serial 2358 error_code 13 request_code 56 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Jonny

---

### Post by fabounet on 2010-09-23
> Hi been trying it actually, but it wont work properly with hyper links 
it does
you can either create a launcher with a command like "firefox http://my-url"
or use the Stask applet, where you can drop any files and weblinks for easy access.

---

