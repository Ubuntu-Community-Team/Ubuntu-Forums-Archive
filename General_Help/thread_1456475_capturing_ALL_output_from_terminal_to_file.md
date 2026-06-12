---
title: "capturing ALL output from terminal to file"
date: 2010-04-17
forum: General Help
---

### Post by linuxcss on 2010-04-17
I would like to capture all output spewed to a terminal session
including processes that are terminated that were invoked from a script
running in a terminal window.

this is beyond capturing just stderr and stdout ....

for example

{
./script 
} 2> stderr.cap 1>stdout.cap

if script is terminated (including because of memory violations)
I get spewed output to the terminal ...
I would like to capture that spewing to a file automatically or to a bit
bucket /dev/null

Is there another filehandle which can be redirected to do this?
If so how or is there another way???

---

### Post by philinux on 2010-04-17
snip

---

### Post by linuxcss on 2010-04-17
philinux

'snip' ????

---

### Post by falconindy on 2010-04-17
> **linuxcss said:**
> philinux

'snip' ????
Probably means he had an idea and then realized it wouldn't work. There's no way to delete a post on these forums.

'script' might do what you want.

---

