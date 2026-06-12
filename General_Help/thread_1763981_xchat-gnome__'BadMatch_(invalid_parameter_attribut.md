---
title: "xchat-gnome:  'BadMatch (invalid parameter attributes)'"
date: 2011-05-21
forum: General Help
---

### Post by nzc3 on 2011-05-21
Dear Community,

I am posting right now as I have encountered an error which I could not solve with the various threads I did find via internet.

Here comes the problem description; hope somebody can help :-k:

[PROBLEM]
* I did set up xchat-gnome and wanted to test transparency 
  within the window, so I did configure it within the 
  xchat-gnome settings.
* it worked fine till restarting the application, here it 
  seems to crash (see below the tests).

[TROUBLESHOOTING]
* I did check the net for crashes, problem etc. and 
  encountered a BUG report for a problem, which I do confirm 
  is the same as mine:

[https://bugs.launchpad.net/ubuntu/+source/xchat-gnome/+bug/277693](https://bugs.launchpad.net/ubuntu/+source/xchat-gnome/+bug/277693)

* As you can see this was for version:
  8.10

  mine actually is:
  2.6.38-8-generic #42-Ubuntu SMP 
  Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

  x@x-x:~$ cat /etc/issue
  Ubuntu 11.04 \n \l


* also a workaroud is being described within the BUG report 
  which states to use gconf-editor (via ALT+F2) to nchange the   
  parameter:
  background_transparency setting it to 0.

* when tryng this:
    a) it does not work
    b) parameter is automatically set to:
       1.1754943508222875e-38  (in case I change 
                                it to 0 manually)

[NOTE]
On my machine when doing a:
xchat-gnome --sync
I do receive:
-----------------------
x@x-x:~$ xchat-gnome --sync
The program 'xchat-gnome' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 961 error_code 8 request_code 56 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
-----------------------

[EXPECTATION]
I hope somebody can help on this one as expected solutions do not work, as for now.
In case I need to submit a bug report, let me know and I will escalate via "launchpad"

PS:  
I am using xchat right now so it is not a real problem, but just want to fix this out of "technical ambition" :D

Greetings to all
nzc3

---

### Post by dhasenan on 2011-06-04
Use gconf-editor and remove the path to your background image.

---

### Post by nzc3 on 2011-06-05
Dear dhasenan,

I apreciate your answer. It has solved completely the problem I was having and xchat-gnome is now completely accesible.

I did the following for clarification:

1.) ALT+F2
2.) executed comand:  gconf-editor
3.) went to:  apps --> xchat --> main-window
4.) did set "background_type" from "1" to "0"
5.) saved and
6.) executed xchat-gnome

Thanks again for the answer and for the help given, I appreciate it.

Greetings to the community
nzc3

---

