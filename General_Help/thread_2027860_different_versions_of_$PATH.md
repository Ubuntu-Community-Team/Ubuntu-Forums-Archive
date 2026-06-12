---
title: "different versions of $PATH?"
date: 2012-07-17
forum: General Help
---

### Post by engine on 2012-07-17
I've installed a new version of the mup score-writing package, and updated my .bashrc accordingly:

echo $PATH in a console returns what I'd expect, with my new usr/local/bin/mup6-0/bin at the end

:echo $PATH in a vim session returns a different version of $PATH, without the subdirectory, so I can't use ! to run the mup command from inside vim.

What file do I have to find and update in order to make sure vim finds the mpu command in usr/local/bin/mup6-0/bin?

Thanks in advance!

---

### Post by prshah on 2012-07-17
> **engine said:**
> and updated my .bashrc accordingly:

echo $PATH in a console returns what I'd expect,

:echo $PATH in a vim session returns a different version of $PATH, 

using pling (!) in vim to spawn a shell probably runs a different shell from bash (maybe sh?), so your .bashrc will not be processed.

To make a global change, consider putting your change in the /etc/environment file (create if not present).

---

### Post by engine on 2012-07-22
Thanks! I've been looking forward to trying this tip … and it has done just what I hoped for. I'll cross-post it to the Vim forum, since no-one there managed to come up with a clear answer <g>

---

