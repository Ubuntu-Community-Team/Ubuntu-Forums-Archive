---
title: "Lubuntu/windows7. grub"
date: 2010-10-26
forum: General Help
---

### Post by næl on 2010-10-26
Hello. I need some help. I am a noob so i need it easy. And my english  is not any good but i ll try. I installed windows 7 and lubuntu 10.10.  It worked like it have always done (use to have win7/lubuntu 10.04. But  when i updated the ubuntu img (i think) windows boot got over written.  So I fixed windows boot, and as always it deleted lubuntu boot. So i  came here and used this guide: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) , But now  windows boot got deleted. So I guess I in some kind of evil circle.

---

### Post by rattamayhorka on 2010-10-26
let me undersand do you want both windows bootloader and the grub (linux) runing at the same time? thats not ok. what you need is grub menu with windows 7 and linux entries when you boot and then you can pick one.
just like this:

[IMG]http://www.dedoimedo.com/images/computers_new_2/grub2-dual-boot-in-grub2.png[/IMG]

if you want to do this look at this page is good. [http://www.dedoimedo.com/computers/grub-2.html]("http://www.dedoimedo.com/computers/grub-2.html")

---

### Post by næl on 2010-10-26
> **rattamayhorka said:**
> let me undersand do you want both windows bootloader and the grub (linux) runing at the same time? thats not ok. what you need is grub menu with windows 7 and linux entries when you boot and then you can pick one.
just like this:

[IMG]http://www.dedoimedo.com/images/computers_new_2/grub2-dual-boot-in-grub2.png[/IMG]

if you want to do this look at this page is good. [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

Yes thanks. It looks like an easy fix.

---

### Post by næl on 2010-10-26
Nope no success... any one

---

### Post by oldfred on 2010-10-26
Full chroot reinstall of grub2 usually  works.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


You may have to install the osprober also to get it to find windows:
[http://ubuntuforums.org/showthread.php?t=1604264&highlight=lubuntu](http://ubuntuforums.org/showthread.php?t=1604264&highlight=lubuntu)

---

### Post by oldfred on 2010-10-26
I see you already have the same answer.

Please do not double post.

[http://ubuntuforums.org/showpost.php?p=10028187&postcount=277](http://ubuntuforums.org/showpost.php?p=10028187&postcount=277)

---

### Post by næl on 2010-10-26
> **oldfred said:**
> I see you already have the same answer.

Please do not double post.

[http://ubuntuforums.org/showpost.php?p=10028187&postcount=277](http://ubuntuforums.org/showpost.php?p=10028187&postcount=277)

Sorry. Was unsure where to post. I will follow up on the other post. thanks

---

### Post by næl on 2010-10-26
**Re: Grub/XP/Vista Bootloader**             
                                                                     Quote:
                                                                      Originally Posted by **næl**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10028187#post10028187")                 
                 *But now windows boot got deleted. So I guess I in some kind of evil circle.*
                                 
It may appear that it is an evil circle, but perhaps not. Perhaps  the windows boot is still there (well, the boot files) but Grub hasn't  seen Windows yet. The reason is that Lubuntu doesn't come with the  software that searches for the Windows partition. You have to install it  before Grub will find Windows.

So, if you are now booting to Ubuntu normally, without the LiveCD, open a terminal and run this command to install *os=prober*
     Code:
     sudo apt-get install os-prober 
Once it is installed, update Grub. 
     Code:
     sudo update-grub 
Now see if Windows is in your Grub menu:
     Code:
     grep "menuentry" /boot/grub/grub.cfg 
If it is, reboot, choose Windows and see if it will boot. 

If it isn't there, or if Windows won't boot, then please run the boot  info script from the following link and post the contents of the  RESULTS.txt that it produces. This will allow us to see the boot status  of Windows and Ubuntu and figure out how to fix your dual-boot system.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

[[COLOR=#D40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")

---

