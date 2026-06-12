---
title: "How to boot multiple OpSys"
date: 2009-12-23
forum: General Help
---

### Post by ttoilleb on 2009-12-23
While researching Ubuntu and trying to decide how to set it up, I ran across the following post in the JustLinux.com forums.  After reading it multiple times, I setup one of my desktops as described in the post and it works great.  The desktop is now set to boot 8.04 or 9.04 (now the primary) and when 10,04 is released, I will install it into the 8.04 partition to test.

While this post is from 2006 and discusses installing 145+ operating systems, it is just as valid for 2 or 3.

[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

---

### Post by dcstar on 2009-12-23
> **ttoilleb said:**
> While researching Ubuntu and trying to decide how to set it up, I ran across the following post in the JustLinux.com forums.  After reading it multiple times, I setup one of my desktops as described in the post and it works great.  The desktop is now set to boot 8.04 or 9.04 (now the primary) and when 10,04 is released, I will install it into the 8.04 partition to test.

While this post is from 2006 and discusses installing 145+ operating systems, it is just as valid for 2 or 3.

[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

And since Ubuntu now uses Grub2 the information in the link is no longer relevant.

---

### Post by oldfred on 2009-12-24
I followed that thread at justlinux and it is still somewhat relevant. I had to force grub2 to install into a partition even though it is not recommend as it has to use blocklists for my karmic alpha install. And I am booting grub2 from the mbr and then chainbooting to my grub partition to chainboot all the old grub version systems I still have.

---

