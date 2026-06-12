---
title: "Asks for password to mount anything"
date: 2012-09-06
forum: General Help
---

### Post by fallenshadow on 2012-09-06
All of a sudden Ubuntu 12.04 asks for a password to mount any device.

I have been trying solutions online but nothing has worked so far.

Anyone have ideas for a fix? D:

---

### Post by zombifier25 on 2012-09-06
Can you post the content of /usr/share/polkit-1/actions/org.freedesktop.udisks.policy on Pastebin? Have you changed DE, user account, anything etc.?

---

### Post by fallenshadow on 2012-09-06
Here you go:

[http://pastebin.com/59TDZush](http://pastebin.com/59TDZush)

Haven't changed DE or user account etc.

---

### Post by fallenshadow on 2012-09-06
Ok for the non-admin account mounting works fine without password.

Problem is just with my account which is admin.

Today I did this:

> sudo visudo

I then put this in the file:

> %myUsername ALL = NOPASSWD: /bin/mount
%myUsername ALL = NOPASSWD: /bin/umount


This has had no effect on my mounting of devices. :/

---

### Post by fallenshadow on 2012-09-11
Anyone had this issue before?

I want to solve this as best I can without doing a reinstall of 12.04. 

Should I reinstall the udisks package to get a new default config?

---

