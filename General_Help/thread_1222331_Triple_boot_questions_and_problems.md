---
title: "Triple boot questions and problems"
date: 2009-07-24
forum: General Help
---

### Post by pwhipped on 2009-07-24
I finally got windows 7, vista, and ubuntu all installed and "semi"-working. I installed ubuntu, then win 7, and then vista. I had win 7 dual booting correctly with grub. I then installed vista (I know out of order). I have everything working correctly it seems, grub shows the windows loader I put in, referenced to win 7. The problem is, when I choose win 7 in grub it boots to vista, but not before showing the bootloader of windows. In other words, the bootloader is working correctly (it shows vista and windows 7), but I have no time to choose anything other than vista. I imagine vista just put its bootloader in win 7's. Would something like easybcd fix it? Is there any way to separate vista and win 7 and boot them through grub without windows bootloader? Also, referencing the vista partition in menu.lst causes boot mgr missing or whatever that error is. Thanks for any help ahead of time. :)

---

### Post by akakingess on 2009-07-24
Have you done a search on the forums for this problem, because I could have sworn I just saw this exact same issue posted within the last two days, and that post may have your solution already. If I had the time I would find the link for you, but I gotta head in to work. Sorry I couldn't be of more assistance.

---

### Post by pwhipped on 2009-07-24
As embarrassed as I am to say it, that post you saw was probably mine. I had a completely different issue back then. Thanks for the reply though. :)

---

### Post by akakingess on 2009-07-24
Sorry about that, didn't mean to offend in any way, just trying to help as much (or little, depending on how you look at it) as I can on my way out the door. I hope you find a solution and will check again when I get into work and see if I can actually assist. Hang in there!!!

---

### Post by synapsys on 2009-07-24
Some people have been able to boot all three from grub. You will have to play around with it a little. You need to map the partitions in order to trick windows into thinking it is on the first partition of the first hard drive in order to boot from grub. It would be a whole lot easier to boot to vista, use easybcd (like you mentioned) and increase the timeout. This will give you plenty of time to choose vista or 7. Or you may be able to reinstall grub and it may automagically detect your windows partitions.

---

### Post by pwhipped on 2009-07-25
> **synapsys said:**
> Some people have been able to boot all three from grub. You will have to play around with it a little. You need to map the partitions in order to trick windows into thinking it is on the first partition of the first hard drive in order to boot from grub. It would be a whole lot easier to boot to vista, use easybcd (like you mentioned) and increase the timeout. This will give you plenty of time to choose vista or 7. Or you may be able to reinstall grub and it may automagically detect your windows partitions.

:D I booted vista, installed easybcd, and then increased the timeout. That fixes everything. Thanks for the help guys. Can someone point me to a tutorial on partition mapping , especially in its relationship to windows?

---

### Post by synapsys on 2009-07-25
Here's one for win2k, same principal.

[http://www.weiqigao.com/blog/2004/01/14/windows_on_the_second_hard_drive_linux_on_the_first.html](http://www.weiqigao.com/blog/2004/01/14/windows_on_the_second_hard_drive_linux_on_the_first.html)

---

