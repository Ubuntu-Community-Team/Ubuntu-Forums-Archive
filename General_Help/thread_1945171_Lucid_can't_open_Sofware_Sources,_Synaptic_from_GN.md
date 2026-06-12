---
title: "Lucid: can't open Sofware Sources, Synaptic from GNOME, Update Manager hangs"
date: 2012-03-22
forum: General Help
---

### Post by hoink on 2012-03-22
Hey peeps.  Like the subject says, I can't open Sofware Sources, Synaptic from GNOME and Update Manager hangs when I try to DO anything.  I've done a fair bit of searching, but nothing seems to work.

I'm not sure when this started happening, but it might've been after I customized a theme (?) or chose a different default theme.

Here are my symptoms.


-- Choosing Software Sources and Synaptic Package manager causes taskbar to display  "Starting Adminstrative Application..." and then taskbar item disappears and nothing happens.

-- sudo synaptic (and gksu synaptic) has a weird delay (see below), produces a warning then opens and works correctly (this is the warning: "Warning, failed to load: package-supportedUnrecognized image file format".  There's no space between -supported and Unrecognized.)  Synaptic seems to be running slowly.

-- System Testing seems to hang with no acvitity on "gathering information".  (No change after 15 minutes.)

-- Any sudo command, even 'ls' has a weird five-second pause, even on the 2nd run (after I've entered my password).

-- apt-get commands produce no errors

-- In Update Manager (which opens)clicking Settings..., Check or Install Updates causes hang and Update Manager must be "Force Quit"

-- sudo apt-get update && sudo apt-get dist-upgrade successfully update my system


Any advice?

---

### Post by ajgreeny on 2012-03-22
Try terminal command ```
gksu synaptic
```(not **sudo** for gui applications) and see if there are any error messages appearing in terminal from that.

---

### Post by hoink on 2012-03-22
Thx for your reply.

First of all, I edited my OP to fix a typo (gksu synaptic).

Then, I REtyped gksu synaptic to see if the behavior I reported in the OP had changed.  And, by jing, it had.  (I think it was after a fresh reboot.)

Instead of acting like I initially described, gksu synaptic made the "Starting Administrative Application..." taskbar appear, disappear and then hang the command line.  No errors.

I CTRL-C'd, repeated same command, got same result.

I then did "sudo synaptic" and synaptic opened in the same way described in the OP.  I closed it.

Then, I RERAN gksu synaptic, and THEN it opened as described in the OP.

TL;DR - after sudo-ing synaptic open, gksu synaptic worked again with no errors

---

### Post by hoink on 2012-03-23
I should also point out that clicking "Check" on the Update Manager triggers that "Starting Administrative Application..." taskbar effect.

---

### Post by ajgreeny on 2012-03-23
> **hoink said:**
> I should also point out that clicking "Check" on the Update Manager triggers that "Starting Administrative Application..." taskbar effect.
That is quite normal.  Type your password and away you go!

---

### Post by hoink on 2012-03-24
Thx for your reply, but I was referring to the "taskbar thing appears, disappears, then hangs" behavior I described in the OP.

---

### Post by charlesopondo on 2012-04-03
Did you update recently. I'm experiencing similar behaviour after an update and I suspect it could be related to this: [http://ubuntuforums.org/showthread.php?t=1634162]("http://ubuntuforums.org/showthread.php?t=1634162")

---

