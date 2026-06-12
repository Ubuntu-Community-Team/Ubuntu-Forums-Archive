---
title: "All Characters on Login Screen are Boxes"
date: 2010-02-07
forum: General Help
---

### Post by skrimpy on 2010-02-07
I got a new computer yesterday, a 64-bit Asus.  I replaced the power supply and the graphics card immediately.  

I booted the computer up with a spare 20" widescreen monitor on a portable desk to install Ubuntu and make sure all was well with the newly installed power supply and graphics card.

It worked perfectly.

I moved my old tower out from its slot under my desk and put the new Asus tower under there.  I plugged it into my 23" widescreen monitor and booted the computer.

Ubuntu (9.10) boots just fine... but the login screen is all boxes!!  There are no characters, just little white boxes.  I can put in my password and log in.  Once logged in the system is fine - all characters display normally from within Ubuntu.

But the login screen is still messed up.

I cannot fathom what could possibly be going on.  Any help?

---

### Post by skrimpy on 2010-02-07
I solved this issue myself; I had installed some custom fonts in /usr/share/fonts/truetype  - apparently this doesn't work in Karmic as it did in previous versions, so now off to figure out how to install custom fonts without breaking GDM!

---

### Post by audiomick on 2010-02-07
Yes, the boxes are a sign that some font is being specified that can't be displayed.
If you are sorted out, you should put a "solved" tag on the thread. That is available in "thread tools" at the top of the thread.

---

