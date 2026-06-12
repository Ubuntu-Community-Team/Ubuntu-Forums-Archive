---
title: "Anyone else not able to get Openoffice Writer Letter Wizard to work?"
date: 2009-11-01
forum: General Help
---

### Post by jimmy the saint on 2009-11-01
I am running a new Karmic Installation and the letter wizard will not work.  I have JRE6 installed so it should be working.  I am wondering if anyone else has this issue or if it is just me.  I will fiddle around a bit, but if it is a common thing I will file a bug.  If anyone knows how to fix it I would sure appreciate a tip.

Thanks

JTS

---

### Post by skillllllz on 2009-11-01
Look like you found a bug. I'm getting the same thing here. In fact, Letter, Fax, Agenda, and Web Page all do nothing when clicked on.

---

### Post by jimmy the saint on 2009-11-02
I found the solution.  I SWEAR I searched the forums and Google, but it didn't show up until I tried to submit the bug to launchpad.  Apparently, you need to install the package "openoffice.org-java-common" in order to get it to work.

```
sudo aptitude install openoffice.org-java-common
```
will fix the issue.

Hopefully this gets linked as a dependency eventually considering it was brought up in a bug for Jaunty.  Of course, the bug was marked invalid because of a lack of information?  Whatever, it should be installed.

---

### Post by krivine on 2009-11-22
I met the same problem, but didn't have to go quite as far as a bug report to solve it. 

Can you repopen the bug, or provide a pointer? This really ought to be fixed. It's just the sort of thing that anyone switching from Windows would want to use. The fact that it doesn't work, and doesn't give any feedback as to why it isn't working, reflects badly on open source.

---

### Post by Hagar Delest on 2009-11-22
That's because of such method (break an application in different packages) that I stick to the Sun version ([[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)). Same with the themes package for example.

No such troubles with the official version from Sun.

---

### Post by ashvin213 on 2010-02-19
Hi all,
            I had the same issue. Thanks a lot for the fix.
Ashvin

---

### Post by tomdkat on 2010-12-24
I just ran into this issue on Ubuntu 10.10 and installing the above mentioned package did the trick.

Thanks for the info and for starting this thread!  :)

Peace...

---

