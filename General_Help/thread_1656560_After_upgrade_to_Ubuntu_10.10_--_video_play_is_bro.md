---
title: "After upgrade to Ubuntu 10.10 -- video play is brocken"
date: 2010-12-31
forum: General Help
---

### Post by a271828 on 2010-12-31
I have recently upgrade to Ubuntu 10.10.
After restart for very short time I can play videos with 'vlc'... but short video disappears. There is only audio. BTW, video in flash from browser is working. Any other video play fails. 
Totem displays this:
> The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 132 error_code 2 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Any ideas? 
Should I reinstall Ubuntu? (I did not have this issue in Ubuntu 10.04LTS)

---

### Post by bludgard on 2010-12-31
I would try marking Totem and/or VLC for complete removal from Synaptics Package Manager and reinstalling before I reinstalled my OS.
 
One

---

