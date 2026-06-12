---
title: "autologout idle X users"
date: 2012-07-19
forum: General Help
---

### Post by magwart on 2012-07-19
At our facility we have a computer room with more users than computers (Ubuntu 12.04).  Inevitably, someone will leave their computer and walk away, never intending to return.  We need a way to autologout such users so that we can free up the computers for those who need to use them.

In ubuntu 10.04 and 11.04 we used the timeoutd package to provide this functionality.  However, timeoutd doesn't work anymore in Ubuntu 12.04.  I tracked this down to the fact that X logins no longer create new utmp entries (at least not until the first X terminal is is opened).

The 'autolog' package also fails because it does not seem to be able to handle X logins.

Is there a recommended way to autologout X logins in Ubuntu 12.04?  Alternately, is there a good way to determine who is logged into the X console (from this I can roll my own solution) since utmp is not reliable?

---

### Post by magwart on 2012-07-20
It looks like a bug in lightdm is preventing it from updating utmp:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297)

After installing the proposed lightdm update and hacking timeoutd, I was able to get the auto-logout functionality working again.

---

### Post by pravinbravi on 2012-09-23
hi magwart,

can you please write a DETAILED step by step how to. I need to implement this at a motel that have PCs with Ubuntu 12.04 LTS. If we can autologoff after prolonged timed inactivity it will help protect patron's identity and all.

thanks in advance.

TheWickernan666

---

### Post by zerubbabel on 2013-07-05
> **pravinbravi said:**
> hi magwart,

can you please write a DETAILED step by step how to. I need to implement this at a motel that have PCs with Ubuntu 12.04 LTS. If we can autologoff after prolonged timed inactivity it will help protect patron's identity and all.

thanks in advance.

TheWickernan666

It doesn't seem as if this DETAILED "how-to" was ever provided, but it would be VERY HELPFUL! Has anyone else gotten this to work, who could describe the process?

---

