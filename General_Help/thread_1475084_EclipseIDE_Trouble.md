---
title: "EclipseIDE Trouble"
date: 2010-05-06
forum: General Help
---

### Post by Yadda on 2010-05-06
I am having many problems with eclipse. When I install from the repositories it doesn't start... at all. I get the splash screen and then it hangs. When I manually install, I can start eclipse fine but when I go to use the autocomplete eclipse dies. It's just gone. No error, nothing. What could the problem be?

I ran the program from the console and it gives the following error:

> 
The program 'Eclipse' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 37775 error_code 172 request_code 152 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)



Solved: 
this link fixed it:
[http://forums.zend.com/viewtopic.php?f=59&t=5956&p=21030](http://forums.zend.com/viewtopic.php?f=59&t=5956&p=21030)

---

