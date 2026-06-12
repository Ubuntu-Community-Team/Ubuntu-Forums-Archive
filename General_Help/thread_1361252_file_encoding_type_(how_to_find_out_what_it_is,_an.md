---
title: "file encoding type (how to find out what it is, and reset it, recursively?)"
date: 2009-12-21
forum: General Help
---

### Post by junetwo on 2009-12-21
hey there.
is there a way to figure out how a file is encoded (not how it's served from a web server, but rather the file itself how it was encoded when it was saved).

if so, is there a way to set all the files to be encoded in a certain way (eg. utf8)?
im assuming i'd have to just do a find/exec command to do so, but don't know how to figure out the file encoding type.

thoughts?
thanks dudes.

---

### Post by junetwo on 2009-12-23
bump.

---

### Post by falconindy on 2009-12-23
Files are written to disk according to your system wide locale settings. If your locale specifies UTF-8, then everything will be UTF-8.

You can check this by just typing 'locale' at a terminal.

---

### Post by junetwo on 2009-12-25
Rad. Thanks. I got the following on my local server:
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

On my live server, I have:
LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

Any thoughts on how to change them?

---

### Post by junetwo on 2009-12-27
bump.

---

