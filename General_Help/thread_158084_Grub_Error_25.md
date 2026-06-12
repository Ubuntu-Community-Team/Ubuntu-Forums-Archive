---
title: "Grub Error 25"
date: 2006-04-10
forum: General Help
---

### Post by matthen on 2006-04-10
Hello,
I had just sent an email with evolution yesterday when my laptop (Toshiba Satellite) froze- only the mouse worked and nothing responded.
So I rebooted and since I have not been able to boot into my ubuntu system.
It always hangs on:

Grub loading stage1.5 

Grub loading, please wait...
Error 25

I have changed the orders of the boot devices and followed some of the instructions given to people with similar problems, but have not been able to solve my problem.

How can I get ubuntu working again.

---

### Post by mdmarmer on 2006-04-10
25 : Disk read error 
This error is returned if there is a disk read error when trying to probe or read data from a particular disk. 

I think it usually means your /boot/grub/menu.lst is trashed or incorrect

UBUNTU fix. Try running Ubuntu in rescue mode. I believe it was designed exactly for situations like this. Though I'm not sure how to do it exactly I believe rescue mode is the key.

put your installation cd in and type in: "linux rescue" at the boot: prompt.
(ps. You might want to read information on rescue mode by pressing F5 before typing in any commands at the boot: prompt)


Here's a post that may get you on the right track -- it's possible to use auto-completion and guesswork to force grub to boot from a grub> prompt, which you can probably get from the live CD.

[http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=15160&viewmode=flat&order=ASC&start=0](http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=15160&viewmode=flat&order=ASC&start=0)

See also these threads -- you can use the Mepis CD or another method to reinstall grub

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

[http://www.ubuntuforums.org/showthread.php?t=153525&highlight=reinstall+grub](http://www.ubuntuforums.org/showthread.php?t=153525&highlight=reinstall+grub)

Mike

---

