---
title: "GRUB doesn't show list of OS anymore"
date: 2010-04-19
forum: General Help
---

### Post by naurispunk on 2010-04-19
I have been using Ubuntu for a few days and it keeps on surpising me:
This morning when I turned my pc on instead of displaying list of available OS versions GRUB just prints out "[ Minimal BASH-like line...." and console with prefix "sh:grub>".

Why is the list gone and how can i get it back?

---

### Post by lordskid on 2010-04-19
what version of grub / ubuntu are u using?

---

### Post by naurispunk on 2010-04-19
I installed 
Ubuntu 9.10 on a PC alongside Windows XP using Ubuntu installer for Windows.

Grub 1.97~beta4

---

### Post by r_s on 2010-04-19
I think you have a wubi install, 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by naurispunk on 2010-04-19
> **r_s said:**
> I think you have a wubi install, 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

It worked! How did you know that? :D 

Thanks!

---

### Post by r_s on 2010-04-19
> **naurispunk said:**
> It worked! How did you know that? :D 

Thanks!

cheers :)

you wrote you used the ubuntu installer for windows, actually you have your ubuntu installed within your windows. That's a wubi install, but I would  recommend you to install ubuntu in a separate partition, it's hassle free and better.

---

### Post by drs305 on 2010-04-19
This bug has been around for a while now. If you suspect a bug in an app, in addition to searching these forums, you can also visit [Launchpad]("https://bugs.launchpad.net/ubuntu"). 

This site tracks bugs and often the bug reports include solutions by users/developers which haven't yet been incorporated into the package. Click on the "Bugs" link at the top, then enter a term to search for.

For instance, here is the bug report on your issue:
[URL="https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104?comments=all"]
After 9.10 grub update can not boot into Wubi install [/URL]

Using the Launchpad search engine to find bugs isn't always the easiest way to find a solution, but it is an option.

---

