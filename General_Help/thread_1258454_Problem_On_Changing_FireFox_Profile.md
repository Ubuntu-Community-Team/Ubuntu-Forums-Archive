---
title: "Problem On Changing FireFox Profile"
date: 2009-09-05
forum: General Help
---

### Post by chandru155 on 2009-09-05
I installed FireFox 3.5 using Ubuntuzilla two weeks before and today i created another profile in addtion to Default profile. Whenever i change the profile using "firefox -P", i am getting this error. Dont know what to do with this error report. Can anyone help me

```
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 690 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by purgatori on 2009-09-05
This is probably a longshot, but try:

```
firefox -profilemanager
```

... instead.

---

### Post by chandru155 on 2009-09-05
Thanks for the reply. I solved by deleting all the profiles including default profile. And then i created two profiles. Now  they are working fine

---

