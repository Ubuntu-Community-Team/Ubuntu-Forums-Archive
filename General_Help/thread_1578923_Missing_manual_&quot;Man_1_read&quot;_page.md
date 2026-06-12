---
title: "Missing manual &quot;Man 1 read&quot; page"
date: 2010-09-21
forum: General Help
---

### Post by bu2bu on 2010-09-21
Hello

I don't know why but on Ubuntu 10.04 I can't find manual for read bash command (invoked with "man 1 read").

There are manuals for C++ functions, but not for bash command...

However, I'm still able to use that particular command in my scripts.

Is read command deprecated, I miss some files or is this a bug?

Best regards
Chris

---

### Post by lloyd_b on 2010-09-21
> **bu2bu said:**
> Hello

I don't know why but on Ubuntu 10.04 I can't find manual for read bash command (invoked with "man 1 read").

There are manuals for C++ functions, but not for bash command...

However, I'm still able to use that particular command in my scripts.

Is read command deprecated, I miss some files or is this a bug?

Best regards
Chris

There's probably no man page for 'read' for the simple reason that it isn't a command in its own right - it's a built-in function of bash, and information on it is provided in the bash man page.  "man bash" will give you the rather extensive man page for bash, which includes information on all of the built-ins such as 'read'.

Lloyd B.

---

