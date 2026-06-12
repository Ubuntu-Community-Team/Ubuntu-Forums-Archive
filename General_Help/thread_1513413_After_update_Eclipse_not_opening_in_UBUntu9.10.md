---
title: "After update Eclipse not opening in UBUntu9.10 ???"
date: 2010-06-19
forum: General Help
---

### Post by boss_aadi on 2010-06-19
hi...
 i m using Ubuntu9.10, few days back i m updated my system from at that time on wards Eclipse3.4(Galileo) is opening it shows following error...

[B]The program 'eclipse' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 17434 error_code 2 request_code 58 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[/B]

and **Ubuntu Tweak** also not opening from at that time...please help me...
i tried some solutions from Ubuntu forum, but non of them not worked for me....
thanks....

---

### Post by sanderd17 on 2010-06-19
Can you completely reinstall eclipse? If it doesn't work via the repo's, try the eclipse version from the site. Your eclipse settings will be lost (plugins and place of the different subwindows) but your code will remain in the workspace directory.

---

### Post by boss_aadi on 2010-06-19
thanks for ur reply...
ya i m downloaded from eclipse.org , i din't install through the repo's....

---

### Post by boss_aadi on 2010-06-20
2day morning i m install through the synaptic package manager and i m successes, now i am able to work on eclipse.... 
thanks for ur reply......

---

