---
title: "X Window System error"
date: 2009-11-02
forum: General Help
---

### Post by Nick Fiorentini on 2009-11-02
I had posted here...
[http://ubuntuforums.org/showthread.php?t=1308968](http://ubuntuforums.org/showthread.php?t=1308968)
but wasn't able to get a response.  If it's okay, I'd like to post this here...

Hi! I made the switch to all-Ubuntu, all-the-time about two weeks ago and I've found this forum to be a life-saving resource in overcoming issues and answering questions. However, after six or so hours of searching, I'm officially stumped, bewildered, and utterly dumbfounded.

Or something.

I'm trying to learn Python and I get this...
```

Python 2.6.4rc2 (r264rc2:75497, Oct 20 2009, 02:55:11) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from gasp import *
>>> begin_graphics()
>>> The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 243 error_code 14 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
.: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```I've found LOTS of info regarding similar problems, spanning several years, involving many different programs; but I can't find anything that says, "Here's how you fix this!"

If anyone can offer some assistance, I would sincerely appreciate it and promise there will come a day where I will be able to help someone else.
:p

---

### Post by Giblet5 on 2009-11-02
You didn't get a response on either post because that is a generic error that provides absolutely no clue as to what you did, tried, or ran, to get that generic error.

Are you running a python script? Can you post it? Is it part of a supported package or something you wrote?

Too much info is better than none.

---

### Post by Nick Fiorentini on 2009-11-02
> **Giblet5 said:**
> You didn't get a response on either post because that is a generic error that provides absolutely no clue as to what you did, tried, or ran, to get that generic error.

Are you running a python script? Can you post it? Is it part of a supported package or something you wrote?

Too much info is better than none.

Sorry.

All I did was import gasp and "begin_graphics()" as shown above.

What other info should I post?

Thank you!

---

### Post by Giblet5 on 2009-11-02
Doh. Interactive python shell. Sorry.

This appears to be a bug that's specific to Karmic and there's already a [launchpad bug report (409001)]("https://lists.launchpad.net/gasp-dev/msg00061.html") for it.

Some are saying that this only affects systems with certain graphics adapters. I'll confirm that it crashes with an nvidia card on Karmic, but works fine with an nvidia card on Jaunty.

---

### Post by Nick Fiorentini on 2009-11-02
I hadn't seen that bug report.  Thanks Giblet!

After reinstalling gasp and running the latest update, I get a different message...
```
Python 2.6.4 (r264:75706, Oct 29 2009, 15:38:25) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from gasp import *
>>> begin_graphics()
>>> python: ../../src/xcb_io.c:242: process_responses: Assertion `(((long) (dpy->last_request_read) - (long) (dpy->request)) <= 0)' failed.
Aborted
nickf@nickf-laptop:~$ .: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
```

And this is an ATI card on an older laptop (HPdv5139).

So the cure is patience, right?
:D

---

### Post by Giblet5 on 2009-11-02
> **Nick Fiorentini said:**
> I hadn't seen that bug report.  Thanks Giblet!

After reinstalling gasp and running the latest update, I get a different message...

And this is an ATI card on an older laptop (HPdv5139).

So the cure is patience, right?
:D

Apparently! It's nice that the update provides more information when the package crashes. There's that at least. Probably only four or five more updates to go. It's kinda exciting.

---

