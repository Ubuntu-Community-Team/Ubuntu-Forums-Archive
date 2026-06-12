---
title: "Grub2 won't load"
date: 2010-08-02
forum: General Help
---

### Post by TJEnger on 2010-08-02
I recently installed Ubuntu 10.04 alongside Win7. I use Acronis OS Selector to choose which partition to boot. Grub 2 is on sda3 (primary partition on an SSD), not MBR. Win7 uses sda1 and sda2 partitions. I have Grub 2 configured to boot the default distro after 0 seconds, therefore I don't see, let alone have the ability (time) to select anything from the Grub 2 menu.
 
Everything's been working fine, but suddenly Ubuntu won't boot. I just get what looks like an underscore character frozen in the top left corner of a black screen. The hard drive light remains on, but it never boots into Linux. Since Grub 2 is effectively set not to display, I'm not sure whether it even loads.
 
The very last thing I did prior to this happening was to install Komodo Edit 6 which appeared to have worked fine. Following that, I went to re-boot, but it froze. After waiting a while, I manually reset the PC at which point it would no longer boot into Ubuntu.
 
Any ideas?

---

### Post by ubunterooster on 2010-08-02
I say you need to recover grub:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


__________________[SIZE=1][CENTER][Remember; mark your threads as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")
[COLOR=White]"Meddle not with roos; thou art crunchy and grasshopper-like" &#8251;The SABRFL&#8251;[/COLOR][/CENTER]
[/SIZE][CENTER][COLOR=White]UUID = # 31863[/COLOR]
[/CENTER]
 [I] Last edited by ubunterooster; 1 Minute ago
[/I][RIGHT][IMG]http://ubuntucounter.geekosophical.net/img/ubuntu-user.php?user=31863[/IMG][/RIGHT]

---

