---
title: "Files that do change but don't..."
date: 2010-02-16
forum: General Help
---

### Post by parsnipfan on 2010-02-16
Hi, 

So, I have an executable, which at some point said upon execution "Hello, I am an executable file" (It doesn't actually say this, what it actually says is quite tedious)

So I deleted it: $ rm stupidprogram

$./stupidprogram
stupidprogram: command not found

It's gone, good. So copied a new executable to the same directory (and name, but this makes little difference), this one was similar except it would say "Hello, I am a DIFFERENT executable", and this is what happens:

$ cp newexecutable directory/stupidprogram
$ ./newexecutable
Hello, I am a DIFFERENT executable
$ cd directory
$ ./stupidprogram
Hello, I am an executable file

I'm soooo confused.

L

---

