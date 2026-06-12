---
title: "Erratic &amp; random character cursor jumping problem"
date: 2010-12-20
forum: General Help
---

### Post by hpng on 2010-12-20
Hello : 

I have a dv7-4172us laptop from HP, a new laptop..  
It has AMD Phenom II N950 -64 bits processors.
I am running LiveCD version 10.04 LTS 64 bits in "Try Ubuntu" mode.

If I type type fast, the character cursor (not the mouse pointer ) moves away randomly, like a few rows up from present typing location..
Sometimes, something else, like another application scrolls it self
while I am using Gedit to type this posting. the cursor jumps
here and there.

Typing on this forum page also produce the same erratic cursor jumping problems!
 
I also disconnect my optical wireless USB mouse, and still have the same
erratic cursor problem.

[B]I do not have the ANY problems with Win 7 -64 bits.
[/B]This is a serious problem.  It will render any laptop useless with Linux

I so look forward to using Linux....and now this... so very disappointed.
Please advice.   Thanks.

---

### Post by hpng on 2010-12-20
to Try Ubuntu 32 v 10.10 on same laptop.

Wrote this on Text Editor with Ubuntu 32 bits version 10.10.
Well, this is the first time I ran Ubuntu 32 bits on my HP dv7-4173us AMD64 bits Phenom II laptop...

So far cursor is not jumping all over the place.
This might be a 64 bits problems.

At this stage of typing, I notice the same thing with 32 bits Ubuntu as it is with 64 bits Ubuntu.  The cursor is starting to jump here and there.

Wow.. this is unreal.... why?  Why?
If anyone has same problem, please advice..... Thanks.

Here is another observation, When I install Ubuntu 10.10 -32 bit,
on an old Shuttle desktop there is no problem with random jumping of
character cursor when using text editor.  Why why why?
When I was installing Ubuntu to my shuttle desktop, it asked me to choose
the appropriate keyboard type.

However, when installing "Try Ubuntu" ( 64 or 32 bits ) on my HP laptop, 
the installer did not ask me to choose keyboard type.
So, could this be a problem in of incorrect keyboard match on Ubuntu side?
I doubt it.

By the way, I have the same problem with my other HP laptop of same model which I have to return due to screen flickering.......
Again, I do not have any problem with win 7-64 bits.

---

### Post by hpng on 2010-12-20
I also tried to "disable touch pad scrolling" and "disable touchpad while typing" to see if it works.
So far, it appears to solve my problem...
Not sure yet...Will keep my fingers cross.

If anyone of you have a better solution, please let me know.

Oh, what  a night...... 
i am surprise I could not find any solution here.
I did find suggestions on search engines......

---

### Post by jbeale on 2011-01-11
I am using 32bit Lubuntu 10.10 on a Dell Inspiron 9300 laptop (from a flash drive, not installed on the HDD).  It mostly works ok, but when typing in a text window, the cursor sometimes jumps randomly back or up several lines, which is quite frustrating. A few years ago I tried an earlier version of Ubuntu on this same laptop and I do not recall this issue.  Just wanted to mention it here!

---

### Post by hpng on 2011-01-11
Go to touchpad setup. Select disable touchpad when typing text (what else?). IT should help a lot.  now, when you use flash drive for Ubuntu, where do you store your data?  Where is swap partition located? If it is on flash, then it would be really be slow, right?

---

### Post by erkorb on 2011-02-27
I've been having this same issue in Ubuntu 10.4 for a while.  I've tried all sorts of solutions.  However, I noticed that the cursor only jumps when I'm using a web-based applications like ZohoMail, particularly with Firefox.  Perhaps there is an issue with JavaScript based apps and the cursor and Firefox.

Note I'm using Chrome to add this entry and my cursor is working fine.

Any ideas?

Erok

---

### Post by hpng on 2011-02-27
Do this: 

Forgot to mention this:  I am using Ubuntu 10.04 LTS.

```

  
Menu select:
 Systems > Preference > mouse 



Then you get a dialog box with tabs.


In Touchpad tab do this:
 

 Under &#8220;General&#8221; category:
 [Check this box]  Disable Touchpad while typing
 

 Under &#8220;Scrolling category:
 [Check this box]  Disable.
 

 This took care of my problem.
 

 Cheers.
 

 

```

---

