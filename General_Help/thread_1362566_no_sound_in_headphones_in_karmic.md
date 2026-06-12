---
title: "no sound in headphones in karmic??"
date: 2009-12-23
forum: General Help
---

### Post by abhilashm86 on 2009-12-23
there's no sound playing in headphones, why is this happening in ubuntu karmic 9.10? how to resovle it??
i want to remove this ```
abhilash@abhilash:~$ uname -r
2.6.31-16-generic

```  
version of karmic kernel? how do i do that?
i'm unable to select kernel from grub menu at start up??

---

### Post by quixote on 2009-12-24
Sounds like you have two separate questions.  Re the sound issue:  there may be a problem with the alsa driver.  There's quite complete instructions [here]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/") on how to install a newer driver.  That solved my sound problems for me, and maybe it'll help you.

A slightly different method is [here]("http://ubuntuforums.org/showthread.php?p=6589810"), which has the advantage of being easier to update after a kernel upgrade.

About the kernel question: I'd suggest starting a new thread for that one.  When you do, make clear whether you just want to remove the entry that grub shows when you first boot up, or whether you actually want to uninstall that kernel.

---

