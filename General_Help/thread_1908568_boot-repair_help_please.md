---
title: "boot-repair help please?"
date: 2012-01-13
forum: General Help
---

### Post by liquidmonkey on 2012-01-13
having problems booting into ubuntu 11.10 on a samsung series 9 laptop.
used the ubuntu-secured-remix and made a live-cd.
loaded boot-repair and tried to run it but get this message
-- the boot of your pc is in efi mode please change it to bios mode --

how can i do that?

i then did a boot summary which gives me this...
[http://paste.ubuntu.com/803472/](http://paste.ubuntu.com/803472/)

any ideas as to what the problem could be?

---

### Post by Double.J on 2012-01-13
> **liquidmonkey said:**
> 

how can i do that?


Hi there, try having a look in your bios, I don't have that laptop, but this thread may be of interest to you :)

[series 9 natty thread]("http://ubuntuforums.org/showthread.php?t=1737086")

---

### Post by liquidmonkey on 2012-01-13
there was a spot in the bios where efi mode is enabled / disabled.
but just changing that did not do it, i also had to change the option below it which allows win7/vista AND xp to boot. disabling this allows only xp to boot.
not sure why that worked but thought i'd share the info for everyone.

and the main problem was that my HDD was totally full.
i deleted the directory and all was well again!

problem now solved!

---

