---
title: "Change nice priority at launch?"
date: 2010-01-12
forum: General Help
---

### Post by jijin on 2010-01-12
Hello, 

I'm currently running on a really old computer with one proc and little memory. It's just enough to get skype running but it only works well enough if I change the nice level to -5 or lower.

Now the person that uses skype in the house is really the wife, I don't want to teach her how to open htop in command line, fine the pid and then use the correct command to change the nice.

What I am looking for is a script (sorry I don't know thing one about programming/scripting) that will change the nice priority periodically for all pid that are skype. This way call processes will get reniced as well.

I know better then to run it as root/sudo, but I am at a loss (even searches came up with not much) on how to do this.

Thanks in advance, 

-jijin

---

### Post by rnerwein on 2010-01-12
hi
try: sudo nice -n -5 skype (or what else the command for skype is)
ciao

---

