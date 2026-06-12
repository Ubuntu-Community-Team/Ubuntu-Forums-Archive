---
title: "update and partiton"
date: 2010-08-29
forum: General Help
---

### Post by tarek2011 on 2010-08-29
[CENTER][SIZE=3]Hello!!
How are you???
i hope you are fine:wink:
Please I need help
I'm new with ubuntu
there is a partition in my hard disk doesn't appear in ubunto although it appears in windows xp
why??:cry:
and i can't connect to the internet because of motherboard not ubunto
but i want to update ubunto and install games and media players 
how??[/SIZE][SIZE=3]:confused:[/SIZE]
[SIZE=3]thanks for help
bye):P

[/SIZE][/CENTER]

---

### Post by tarek2011 on 2010-08-29
[CENTER][SIZE=3]Hello!![/SIZE]
[SIZE=3] How are you???[/SIZE]
[SIZE=3] i hope you are fine:wink:[/SIZE]
[SIZE=3] Please I need help[/SIZE]
[SIZE=3] I'm new with ubuntu[/SIZE]
[SIZE=3] there is a partition in my hard disk doesn't appear in ubunto although it appears in windows xp[/SIZE]
[SIZE=3] why??:cry:[/SIZE]
[SIZE=3] and i can't connect to the internet because of motherboard not ubunto[/SIZE]
[SIZE=3] but i want to update ubunto and install games and media players [/SIZE]
[SIZE=3] how??[/SIZE][SIZE=3]:confused:[/SIZE]
[SIZE=3]thanks for help[/SIZE]
[SIZE=3] bye):P[/SIZE][/CENTER]

---

### Post by oldfred on 2010-08-29
Please do not double post:

See this thread:
[http://ubuntuforums.org/showthread.php?t=1563823](http://ubuntuforums.org/showthread.php?t=1563823)

---

### Post by oldfred on 2010-08-29
Please do not double post. Info from this thread all should be here:
[http://ubuntuforums.org/showthread.php?p=9782482](http://ubuntuforums.org/showthread.php?p=9782482)


Ubuntu should see all windows partitions. It may not let you mount a windows partition if it needs repair like chkdsk or hibernation that sets flags to prevent damage.

Post this from a terminal:
sudo fdisk -l

Motherboard is not the issue with Ubuntu & Internet. Is the issue an Ethernet hard wired connection or a wireless? Sometimes you have to plug into the Internet with a cable to download the hardware updates for wireless.

---

