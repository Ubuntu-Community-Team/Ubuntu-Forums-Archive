---
title: "corrupt sodoers and unable to boot to single user to fix"
date: 2010-12-24
forum: General Help
---

### Post by strycat on 2010-12-24
So I was messing with my sudoers file and messed it up.  I found this solution:

[http://ubuntuforums.org/showthread.php?t=140852](http://ubuntuforums.org/showthread.php?t=140852)

But the grub menu doesn't appear on boot.  Google finds that ESC, SPACE, TAB, and several other keys are supposed to bring the menu up.  However none work and I can't edit the grub configuration without being able to sudo.  

Is there any solution now short of reinstalling?

---

### Post by sisco311 on 2010-12-24
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by mcduck on 2010-12-24
> **strycat said:**
> So I was messing with my sudoers file and messed it up.  I found this solution:

[http://ubuntuforums.org/showthread.php?t=140852](http://ubuntuforums.org/showthread.php?t=140852)

But the grub menu doesn't appear on boot.  Google finds that ESC, SPACE, TAB, and several other keys are supposed to bring the menu up.  However none work and I can't edit the grub configuration without being able to sudo.  

Is there any solution now short of reinstalling?

Which version of Ubuntu you are running? The latest versions use Grub2, and on that the key to show hidden menu is *Shift*.

---

### Post by noah++ on 2010-12-24
If for some reason you can't boot into single-user mode, there is always the option to *chroot* into your Ubuntu system from a live CD or USB key. There is no need to reinstall.

---

