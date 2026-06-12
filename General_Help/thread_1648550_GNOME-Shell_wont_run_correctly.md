---
title: "GNOME-Shell wont run correctly"
date: 2010-12-18
forum: General Help
---

### Post by u-noob-tu on 2010-12-18
after a ridiculously long install (a little more than an hour), i finally managed to run gnome shell. i didnt want to set it as my default desktop yet, so i ran it from the terminal. it popped up and everything looked alright. i tried to close the terminal and it said the process was still running, which made sense. but when i tried to move the terminal window, gnome shell crashes and brings me back to default gnome. so i ran it again without touching the windows, and it all seemed to work fine. but the moment i touch that window border it dies. i didnt wait for more than an hour to have it crash on me, so i really want to make this work. the terminal gives me his list of errors: 


JS LOG: GNOME Shell started at Sat Dec 18 2010 23:07:29 GMT-0500 (EST)
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:7735): GdmUser-WARNING **: Unable to load CK history: no seat-id found

** (ck-history:7753): WARNING **: Unknown option --since=2010-10-20T04:07:30.213778Z
** (gjs-console:7757): DEBUG: Command line: /home/ryan/gnome-shell/install/bin/gjs-console
** (gjs-console:7757): DEBUG: Creating new context to eval console script
    JS ERROR: !!!   Exception was: SyntaxError: missing ; before statement
    JS ERROR: !!!     lineNumber = '23'
    JS ERROR: !!!     fileName = '/home/ryan/gnome-shell/install/share/gnome-shell/js/prefs/clockPreferences.js'
    JS ERROR: !!!     stack = '@<command line>:1
'
    JS ERROR: !!!     message = 'missing ; before statement'
    JS ERROR: !!!   Exception was: SyntaxError: missing ; before statement
    JS ERROR: !!!     lineNumber = '23'
    JS ERROR: !!!     fileName = '/home/ryan/gnome-shell/install/share/gnome-shell/js/prefs/clockPreferences.js'
    JS ERROR: !!!     stack = '@<command line>:1
'
    JS ERROR: !!!     message = 'missing ; before statement'
SyntaxError: missing ; before statement
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x480002d (seat-id gn); these messages lack timestamps and therefore suck.
Shell killed with signal 11
ryan@ryan-Studio-1737:~/gnome-shell/source/gnome-shell/src$ Unable to open desktop file /home/ryan/Desktop/thunderbird.desktop for panel launcher: No such file or directory
/usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

i am very new at ubuntu so i have no idea what any of this means. please help me out so i didnt lose an hour for nothing.

---

### Post by u-noob-tu on 2010-12-19
*bump* anybody know how to fix this?

---

### Post by defishguy on 2010-12-19
The same thing happened to me yesterday.  Everything I'll try to tell you came from a few minutes spent on IRC figuring out what to do.  I do not necessarily understand everything I'm going to pass along to you but I do know that it worked for me.

I'm assuming you still have your gnome-shell directory and all of the appropriate files in there.

Open a terminal and type:

> /home/%yourusernamehere%/gnome-shell/source/mutter

Now type:

> curl [http://bugzilla-attachments.gnome.org/attachment.cgi?id=176711](http://bugzilla-attachments.gnome.org/attachment.cgi?id=176711) | git am

What you're downloading is a patch that hasn't been put into the main tree yet.

Go to the ~/bin directory. Next you'll want to run:

> jhbuild build

This should go pretty quickly, it did for me.  You will probably get errors as it works,  I told it to ignore the errors and continue.  After it completed in a few moments everything started working again, and working well.  There are a few improvements in there.

I hope it helps.

---

### Post by u-noob-tu on 2010-12-19
> **defishguy said:**
> The same thing happened to me yesterday.  Everything I'll try to tell you came from a few minutes spent on IRC figuring out what to do.  I do not necessarily understand everything I'm going to pass along to you but I do know that it worked for me.

I'm assuming you still have your gnome-shell directory and all of the appropriate files in there.

Open a terminal and type:



Now type:



What you're downloading is a patch that hasn't been put into the main tree yet.

Go to the ~/bin directory. Next you'll want to run:



This should go pretty quickly, it did for me.  You will probably get errors as it works,  I told it to ignore the errors and continue.  After it completed in a few moments everything started working again, and working well.  There are a few improvements in there.

I hope it helps.

thanks, but the terminal keeps rejecting the curl command, says there is nothing to do. i checked the link, it is working.

EDIT: got it to work. had to type each part of the command seperately.

---

### Post by defishguy on 2010-12-19
Excellent!  I'm glad that you got it working.  Have a great Holiday season!

---

### Post by u-noob-tu on 2010-12-19
> **defishguy said:**
> Excellent!  I'm glad that you got it working.  Have a great Holiday season!

thanks, you have a great holiday season too! gnome shell is being built right now. two more questions though: if i want to get back to gnome panels, what command could i use? and if i wanted to make gnome my default desktop again, how would i do that?

EDIT: found a tool called "gnome3-session" that will allow you to choose between gnome 3 (gnome-shell) or gnome panel at login.

---

