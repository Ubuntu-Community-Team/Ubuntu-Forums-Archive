---
title: "Command Line Flag Parameters"
date: 2011-01-19
forum: General Help
---

### Post by commandline39 on 2011-01-19
To launch Chrome I can type "chrome %u" in the command line and it launches. What does the %u do? I've also seen %s and wonder the same thing?

Also, are these called flags and is there a tutorial somewhere on command line flags? I've googled for an hour and can't find "%u" anywhere! Help, thank you :)

---

### Post by sisco311 on 2011-01-19
They are called field codes. They don't have any special meaning in the shell (terminal), only in .desktop files.

Check out: [http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

**The Exec Key** section contains a list of recognized field codes.

---

### Post by commandline39 on 2011-01-21
Perfect, just what I wanted. Thank You!

---

### Post by sisco311 on 2011-01-21
You're welcome!

---

