---
title: "Tomboy Filenames Don't Show"
date: 2010-05-03
forum: General Help
---

### Post by wmichaelb on 2010-05-03
Hi, I installed and tried to use Tomboy for the first time today. (Ubuntu 9.04/Gnome). I created a note, added some information, and then tried to find a way to save it. But there is no "save" choice that I could find, so I simply closed the application, reopened it, and tried to search for the note that I'd just created. Tomboy did not find it. I next tried to create a new note with the same title; but Tomboy tells me that there is already a note with that name. But it will not find it or display it.

What am I missing here? Thanks in advance.
:confused:

---

### Post by ajgreeny on 2010-05-03
So what do you see when you start tomboy, either from the menu or from the icon on your panel?  There is usually a small window with a list of notes you have made as in my screenshot of notes I made today just to remind myself.

I used to use tomboy, but don't find the need any more, though I think it could be very useful in some circumstances.

---

### Post by wmichaelb on 2010-05-03
Hi, thanks for replying! I get the small dialog box, but with only two notes: "Start Here" and "Using Links in Tomboy". If I search for my original note title, I get nothing.

---

### Post by sharm on 2010-05-06
> **wmichaelb said:**
> Hi, thanks for replying! I get the small dialog box, but with only two notes: "Start Here" and "Using Links in Tomboy". If I search for my original note title, I get nothing.

How did you create your note?

Do you still have this problem if you make a new note using File->New Note, then quit Tomboy and start it up again?

If so, please start Tomboy from a terminal using the command `tomboy --debug`, create a note, wait 10 seconds, then save the output you see in the terminal.  There might be some useful error messages.

---

### Post by wmichaelb on 2010-05-07
sharm: thanks for replying! I tried creating a new note, closed and reopened Tomboy, and found the new note immediately. So, just for fun, I ran:

sudo tomboy --debug

At the end of the run, I got the message:

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

This doesn't sound good; perhaps I should uninstall/reinstall?

---

### Post by sharm on 2010-05-07
> **wmichaelb said:**
> sharm: thanks for replying! I tried creating a new note, closed and reopened Tomboy, and found the new note immediately. So, just for fun, I ran:

sudo tomboy --debug

At the end of the run, I got the message:

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

This doesn't sound good; perhaps I should uninstall/reinstall?

1) Don't use "sudo"
2) Without the complete output, I can't know why Tomboy crashed, but it could very well be because you ran with sudo.
3) Uninstalling/reinstalling won't do anything

If you run `tomboy --debug` (without sudo this time) a couple of more times, I'm guessing you won't see any more crashing.

Do let me know if you run into any more problems. :-)

---

### Post by wmichaelb on 2010-05-07
sharm: it seems to be working now. I am missing the couple of notes that I made before "debugging"; even a full search doesn't show them, but it's not the end of the world. 

Thanks for the tip!

---

