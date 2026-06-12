---
title: "sudo dpkg-reconfigure -phigh -a Fails"
date: 2012-01-07
forum: General Help
---

### Post by Lyuokdea on 2012-01-07
My ubuntu installation has gotten really messed up (freezes while booting to the desktop) - but I can still get in via ssh, and everything seems to be working ok there. I want to try to reinstall using:

sudo dpkg-reconfigure -phigh -a

But then I get an error:

dpkg-maintscript-helper: error: couldn't identify the package

upon which reconfigure closes. 

Is there any way to fix this? I could do a complete reinstall of ubuntu I guess, but I'd like to break as little as possible.

Thanks,

~Lyuokdea

---

### Post by Lyuokdea on 2012-01-07
Anybody have any ideas on this? It sounds like I probably need to do a complete reinstall, but I'd rather not if possible.

---

### Post by Lyuokdea on 2012-01-09
Maybe another way to do it -- 

is there anyway to import a list of nearly all the packages to dpkg-reconfigure ?? Then I can just leave out the package that is breaking, and reupgrade everything else? Where would i get such a list?

---

