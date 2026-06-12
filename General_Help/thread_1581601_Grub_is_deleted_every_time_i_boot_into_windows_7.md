---
title: "Grub is deleted every time i boot into windows 7"
date: 2010-09-25
forum: General Help
---

### Post by ambdeep on 2010-09-25
I have a new dell studio 1558 with core i5 processor and 4 gb ram. I just installed ubuntu 10.04 and every time i boot into my windows 7 partition my grub seems to stop working. The only solution i have found so far is to re-install grub using the live cd, but it is not feasible to do that every boot. Is this a standard problem(or is there a solution to this problem)? Also, I havent updated my ubuntu yet, will that help? Any help would be appreciated.

---

### Post by Gogl on 2010-09-25
I have a Dell Studio XPS 16 (1645) with 10.10 beta and the same issue. I think it's a Dell issue. Couldn't find another solution yet. I have no idea how to identify the reason for this problem.

---

### Post by coffeecat on 2010-09-25
It's one of the Dell utilities that's the culprit here. See:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

More background here:

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable")

Not having a Dell, I haven't seen this myself, but I guess you need to disable whichever Dell utility is causing this. Or follow one of the more drastic steps described in the first link.

---

