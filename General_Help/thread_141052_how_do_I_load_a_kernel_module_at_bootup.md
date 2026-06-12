---
title: "how do I load a kernel module at bootup?"
date: 2006-03-07
forum: General Help
---

### Post by mcpish on 2006-03-07
Hi, I've been using Linux for about 1/2 year now but I still don't understand some of this kernel stuff.

Basically I like to run a file encryption system called "encfs" but I have to always load a kernel module called fuse all the time or it won't work. I can just type "modprobe fuse" on the console and this always works and loads the module, but how do I setup Linux to do this automatically at bootup? I read some directions here before about downloading the fuse sourcecode and "recompiling" my kernel but I kept getting some error messages about it not being able to overwrite certain fuse files which are already on my system.

I understand Linux decently, I'm comfortable in the shell and using apt and editing text/configuratino files and whatnot, but I'm just trying to now learn this stuff about Kernels and Kernel modules and how to setup bootup scripts which I don't understand yet.

Can anyone help me?

---

### Post by christhemonkey on 2006-03-07
Add a line to the end of your /etc/modules
```
sudo vi /etc/modules
```
and add fuse to the end
(if your unfamiliar with vim type ZZ to exit and save or :q! to quit without saving)

---

### Post by mcpish on 2006-03-07
Thanks, that was easy :cool: 

That's the thing about Linux, it's just a matter of learning what all the files do and what they mean.  :)

---

