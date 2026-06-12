---
title: "Ubuntu is gone..."
date: 2011-05-12
forum: General Help
---

### Post by Tom83B on 2011-05-12
I installed the Ubuntu directly from Windows, where it allows you to install it without any partitions. It says it is installed like an application. But now the computer turned of when I was working on Ubuntu, because the battery was low and now it won't load. When I select Ubuntu on start-up, it says something like that it was not found and than there's terminal, where is something like grub>>
I tried Live CD, but it didn't help, probably because the Ubuntu is not installed on a partition.
I really need to get to my data. Do you have any ideas what might work?
Thanks in advance

---

### Post by Jrhw on 2011-05-12
Tom if I read your post correctly it sounds as if you installed Wubi, which allows you to install Ubuntu from within Windows - if this is indeed what you did. I would suggest you look here for your answer [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Rubi1200 on 2011-05-12
Hi and welcome to the forums Tom83B :-)

Be aware that Ubuntu installed inside Windows with Wubi is sensitive to things like hard or unexpected shutdowns, and file fragmentation on Windows.

The link provided by Jrhw is a good place to start. With what you have described, chances are the Wubi root.disk has been damaged. Posting the results of the boot info script mentioned in the main post would be a good start.

@Jrhw; welcome to the forums :-)

---

