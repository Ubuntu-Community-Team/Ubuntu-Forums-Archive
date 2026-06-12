---
title: "Cannot run Eclipse IDE in latest 10.10 update"
date: 2011-07-01
forum: General Help
---

### Post by Sesshomurai on 2011-07-01
Hi,
  Eclipse no longer works in 10.10 desktop 64bit, latest update.
The error:

The program 'Eclipse' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
(Details: serial 10174 error_code 8 request_code 153 minor_code 4)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)

progname=Eclipse; RGBA=on

Any tips?

---

### Post by Gyokuro on 2011-07-01
Which java version are you using and do you use eclipse from repo or from eclipse.org and in this case which version?

---

### Post by Sesshomurai on 2011-07-01
I'm using JDK1.6.0_24

and I downloaded eclipse from eclipse.org because my one from the repo stopped working for same reason.

It used to work, but a couple Ubuntu updates later, they stopped working.

---

### Post by Gyokuro on 2011-07-01
Ok, I'm using the same JDK and the new Eclipse Indigo on Ubuntu 11.04, new Eclipse Indigo on Ubuntu 10.04 LTS but with JDK 1.6_26 (latest Oracle JDK), all 64-Bit and error do not happen - is it possible that this error got already posted on the eclipse forum ([http://www.eclipse.org/forums/index.php/m/691610/)?](http://www.eclipse.org/forums/index.php/m/691610/)?) 

I have tried the new eclipse Indigo with latest Oracle JDK on RHEL 6.0 and 6.1 and it works but I can not test on 10.10 as I do not use this release. Are you aware which updates you have applied to your 10.10 installation?

However I can only suggest to stick with an Ubuntu LTS release and the official JDK from Oracle.

---

### Post by Sesshomurai on 2011-07-01
Hi Gyokuro,
   Thanks for checking. Yes, that was also my post on Eclipse forum. :)

I guess I should update a few things and see if that fixes it.Its just odd that only Eclipse fails in this instance and I never seen this error before.

I appreciated the tips. Thank you.

---

