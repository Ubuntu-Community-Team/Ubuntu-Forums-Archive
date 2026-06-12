---
title: "GIMP Slowness"
date: 2006-03-11
forum: General Help
---

### Post by Raeth on 2006-03-11
Greets,

I have my Wacom Graphire 4 tablet working on Linux (Ubuntu 6.04,
kernel 2.6.15, built-in tablet drivers) and get bad pressure sensivity
and line quality in The GIMP 2.2.10, but at least it's working.

However, when using any of the paint/ink tools, although producing a
decent stroke, it fails to keep up. The stroke does not lag as if on a
slow system, but if I end a stroke and quicky make another stroke, the
second stroke does not appear.

I notice that the CPU goes up to 100% whenever I paint with the
paint/ink tool, and there's a slight cursor-lag at the end of each
stroke, which I guess is why the system is not catching the next one.

I'm sure this is not due to GIMP's inefficiency, as it works fine on
my friend's much slower computer.

Can anyone help?
Thanks, Raeth

Note: I've not yet tried the tablet using the downloaded driver source
code, due to the X.org SDK not existing for Ubuntu.

---

### Post by jerrykenny on 2006-03-11
you may just need more memory ? I think you can free some up by telling gimp not to store so many undo steps.

---

### Post by Raeth on 2006-03-12
Thanks, it does seem to be the speed at which is saves the undo steps. I have plenty of RAM, but it is about 10 times slower than modern RAM.

However I believe it is GIMP's problem, because Photoshop handles it fine.

---

### Post by stoffe on 2006-04-27
Got the same problem here, and filed a bug at [https://launchpad.net/distros/ubuntu/+source/gimp/+bug/41798/](https://launchpad.net/distros/ubuntu/+source/gimp/+bug/41798/)

Any news since this was posted?

---

### Post by haydxn on 2006-12-11
I have this exact same problem, and it's driving me batty. I wish I could find a way around this.. I moved back to ubuntu from using Gimp in Windows [because pressure sensitivity support for my wacom just isn't present there], and now I find this problem! Maybe I'll just switch back... :(

---

### Post by gottferdamnt on 2007-04-15
UP! Gimp is also too slow with my graphire 4 on feisty... CPU usage at 100%.  Is this issue was or will be fixed?

---

