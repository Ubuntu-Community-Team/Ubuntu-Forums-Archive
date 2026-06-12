---
title: "Uninstall Ubuntu"
date: 2010-01-07
forum: General Help
---

### Post by topdog2009 on 2010-01-07
I have Ubuntu installed as a dual boot. It was installed from the live CD and I have a Directory in my C drive called Ubuntu and my hard drive was partitioned during (or prior) to the install. I am using Windows XP

How do I:

Uninstall Ubuntu (can I just go to Add/Remove programs in Windows to do that) or what.

Remove the repartitioning.

Stop the dual boot attempt.

Thanks

---

### Post by oldos2er on 2010-01-07
It's not clear whether or not you're using Wubi. If so, you should be able to use Windows' Add/Remove to uninstall it.

If you have Ubuntu installed to its own partition, run Windows' fixmbr command, reboot, then you should be able to safely remove/reformat the Ubuntu partition.

---

### Post by fancypiper on 2010-01-07
If you did a Linux install, perhaps this will help:

[How to Remove Linux and Install Windows XP on Your Computer](http://support.microsoft.com/kb/314458/EN-US/)

---

### Post by topdog2009 on 2010-01-07
> If you did a Linux install, perhaps this will help:

[How to Remove Linux and Install Windows XP on Your Computer]("http://%22http//support.microsoft.com/kb/314458/EN-US/")

This link does not work but thanks - I did a WUBI install

---

### Post by oldos2er on 2010-01-07
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by topdog2009 on 2010-01-07
Thanks - subsequent to the last posting, I found this link.

Ubuntu now removed.

Thanks to all who endeavoured to help me, unsuccessfully, to get this up and running on my machine. This community is great.
:popcorn:

---

### Post by fancypiper on 2010-01-07
I'm glad you were helped.  Linux runs best on it's own flle systems, BTW, so don't give up.  Open Source is improving by leaps and bounds.

[Mark Your Thread as [SOLVED] After Getting Your Answer](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

