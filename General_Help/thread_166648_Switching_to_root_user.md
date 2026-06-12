---
title: "Switching to root user?"
date: 2006-04-26
forum: General Help
---

### Post by kyoushu on 2006-04-26
How do I switch into the root user?  I try logging in with username root and my password, but it says I can't login from that login screen.  How else can I login(if through the terminal, how?)?

---

### Post by mjm115 on 2006-04-26
Have a look here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

You usually don't want to log in as root.  This is a HUGE security risk.

---

### Post by rvergara on 2006-04-26
Just do a search for root or sudo in the forum.

There are literally thousand of entries on the subject.

My recommendation is NOT to use root at all. You can accomplish all admin chores via sudo and it is a lot safer.

Regards

Ramiro

---

### Post by kyoushu on 2006-04-26
I understand the risks, and it's only so I can easily copy some files into a folder.  Thanks a bunch.

---

### Post by sinkxdie on 2006-04-26
Good, thats safe, and It's the only reason I log in as root too.
But DONT open up any graphical programs.

---

### Post by kyoushu on 2006-04-26
Well, another thing is, I have a problem with my network so there's no real security problems considering Im not even connected to the internet, and may never be.

---

### Post by aysiu on 2006-04-26
[QUOTE=kyoushu]I understand the risks, and it's only so I can easily copy some files into a folder.  Thanks a bunch.[/QUOTE] You want easy, press Alt-F2 and type ```
gksudo nautilus
``` Logging in as root is not easier than that, I assure you.

---

### Post by nanotube on 2006-04-26
to clarify aysiu's post, "gksudo nautilus" will start up a file browser in root mode for you, so you can copy anything to anywhere. (as well as delete anything, and screw up anything - so be careful :) ).

---

