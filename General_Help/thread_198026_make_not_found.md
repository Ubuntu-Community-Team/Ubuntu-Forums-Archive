---
title: "make not found???"
date: 2006-06-16
forum: General Help
---

### Post by synecdoche on 2006-06-16
I am trying to install k9copy from the source.  After getting all the dependencies, I ran ./configure just fine, but now when I run make, I get make: command not found.  

What's going on here?  This is one error I've never seen in any linux distro. Do I need to install something else? 

Thanks.

---

### Post by aysiu on 2006-06-16
Yes, you need to install *build-essential*. Pop in the Ubuntu CD (either the Desktop or Alternate) and type ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
``` Read more about why it's not installed by default [here](http://www.ubuntuforums.org/showthread.php?t=192840). I haven't heard a convincing reason yet, but the reasons are there--convincing or not.

---

### Post by bruce89 on 2006-06-16
*(beaten to it again)*, incidentally, I saw an option to delete a post earlier today, where has it gone?

---

