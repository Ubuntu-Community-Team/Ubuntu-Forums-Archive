---
title: "Totem Closing"
date: 2011-05-24
forum: General Help
---

### Post by Hman242 on 2011-05-24
Totem has been closing when I try to use it to play anything. The program opens fine, but closes when trying to play something. When running via Terminal, I get this.
```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 185 error_code 2 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```How to I go about fixing this? I would prefer to fix the problem than switch to a different player, as I like Totem.

---

### Post by no2498 on 2011-05-24
see if you can run this

in a terminal type gstreamer-properties click enter

if it comes up click video
set the plugin to x window system no xv

if it dont come up you need gstreamer good,bad,ugly and 10 for your ubuntu/linux you use

---

### Post by Hman242 on 2011-05-24
That worked, thanks man.

---

### Post by no2498 on 2011-05-24
your welcome now mark it solved

---

### Post by etienne@Rofti on 2011-05-29
Thanks!

I had the same problem, on an HP Compaq 615 with ATI Raedon graphics. The same solution worked perfectly. Thanks so much!

E

---

### Post by wmwong on 2011-09-14
I'd just like to add that it also worked for me. Thanks!

---

