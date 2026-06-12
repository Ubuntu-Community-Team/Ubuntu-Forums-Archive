---
title: "OpenOffice crashing, failing to open first attempt"
date: 2009-09-23
forum: General Help
---

### Post by riseringseeker on 2009-09-23
I recently began having a problem with OpenOffice 3.01.  If I go to "Applications -> Office -> OpenOffice.org Word Processor (or Spreadsheet)" the Openoffice splash screen appears, then disappears, then nothing happens.  It simply does not open.  Selecting it a second time always works though (so far).

Also, when I click on an Openoffice file (again, either a spreadsheet or text document) the splash screen again comes up, the program itself starts, and the progress bar does it's thing, but before the file displays, it just closes.  It does this unless I already have a copy of Openoffice open, or if I've already have opened a file (still open or not) prior to clicking on the new file.

This is a real annoyance.  If anyone has any clue, please respond.

---

### Post by mentalelf on 2009-09-23
Maybe running it from a terminal will give you some idea what's wrong, it'll typically output any errors to the terminal window when you run things this way.

Open a terminal, run...

oowriter (for word processor)

openoffice.org (for front-end)

or type oo & hit tab twice, it'll show you the commands to run for each individual program.

---

### Post by riseringseeker on 2009-09-25
> **mentalelf said:**
> Maybe running it from a terminal will give you some idea what's wrong, it'll typically output any errors to the terminal window when you run things this way.

Open a terminal, run...

oowriter (for word processor)

More than a little odd.  When I do the above on my desktop, it opens the word processor after having given an error message.  When I try the same on the laptop, it gives the same error message, but fails to open.

The error message given in both cases is:

```
~$user@either-computer: oowriter

** (soffice:5207): WARNING **: unable to get gail version number

```

> openoffice.org (for front-end)

On the desktop, I get an error message, but the front end opens just fine.  On the laptop I get no error message on the first try, but the front end, though it apparently is open, it's a transparent window with a title bar.  IOW, the only portion showing is the title bar, and the edge of what should be a filled in window.

The error messages I get on the desktop and the laptop on the *second* try are:

```
user@desktop:~$ openoffice.org

** (soffice:1286): WARNING **: unable to get gail version number

```

and:

```
user@laptop:~$ openoffice.org

** (soffice:5456): WARNING **: unable to get gail version number

```

I have compiz running on both, but changing to metacity on either has no effect.

> or type oo & hit tab twice, it'll show you the commands to run for each individual program.

No error message on either doing this, just does what's expected of it.

I will be googleing "gail version" as soon as I finish this reply.  Sorry about not posting earlier, have had out of town guests.

---

### Post by Hagar Delest on 2009-09-26
Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by riseringseeker on 2009-09-27
> **Hagar de l'Est said:**
> Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

Should have mentioned, in searching for solutions in the forums, already tried that to no avail.

---

### Post by Hagar Delest on 2009-09-27
Try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by riseringseeker on 2009-09-29
> **Hagar de l'Est said:**
> Try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

I would rather stick with what's in the repositories.  I've also read a number of problems about installing OO from source, which I would rather avoid.  After all, I have a working install, it's just an annoyance that I have to "open" it twice, or I can't open a document directly without having already opened OO.

Googling for the above error message, it would seem there has been a fix, it just hasn't (and likely won't) make it into a Jaunty install.  9.10 is just around the corner, would be surprised if it did not include the fix.

---

### Post by Hagar Delest on 2009-09-29
Note that it's not installing _from source_. It's just another version of OOo (the Sun one).

---

### Post by riseringseeker on 2009-10-02
> **Hagar de l'Est said:**
> Note that it's not installing _from source_. It's just another version of OOo (the Sun one).

From reading the referenced thread, it sounds like it still may open a can with too many worms for me to want to hassle with, especially since mine **does** work, just not entirely like it should.

As I type, updates for OO came down the pipe this morning and are currently downloading - we'll see if that fixes the annoyance.  It is, after all, more of an annoyance than anything else.

---

