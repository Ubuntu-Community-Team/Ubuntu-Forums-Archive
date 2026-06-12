---
title: "exmh/tcl xauth stops working after update from 8.04 to 10.04"
date: 2010-05-02
forum: General Help
---

### Post by jmeissen on 2010-05-02
I've been using exmh as my mail reader for years. It's written in tcl/tk and uses the tk send facility to communicate with a background process. This communication depends on properly configured Xauthority.

After upgrading from 8.04 to 10.04 I get
 X server insecure (must use xauth-style authorization)

I've removed and re-installed tcl8.4 and exmh to make sure it's not a package problem.

The XAUTHORITY env variable is set up properly. xauth shows the proper cookie:
xauth> list
john/unix:0  MIT-MAGIC-COOKIE-1  9d2c3ae970c352a0d21159190d9e5530

Access control is enabled.

I'm at a loss where/how to proceed. I need to get this working, it's not reasonable at this stage to switch to a different mail client.
:sad:

---

### Post by jmeissen on 2010-05-03
This appears to be a problem with gdm. There is/was a Solaris bug tracker related to this:
[http://http://defect.opensolaris.org/bz/show_bug.cgi?id=13571]("http://http://defect.opensolaris.org/bz/show_bug.cgi?id=13571")

They show it as "fixed", but I don't know what they changed.

How do I report this?

---

