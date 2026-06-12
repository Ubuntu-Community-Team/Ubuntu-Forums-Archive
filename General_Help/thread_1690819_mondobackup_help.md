---
title: "mondo/backup help"
date: 2011-02-19
forum: General Help
---

### Post by Red Kelly on 2011-02-19
[SIZE=2]Hi I am having some dificulty backing up my home server (Ubuntu 10.04 LTS 64-bit)
I have been trying to backup with mondo but am getting stuck with an error somewhere and don't know what it is and what to do.

I have installed the latest from the mondo site by:
[/SIZE]
[LIST]
[*]cd /var/tmp
[*]wget [ftp://ftp.mondorescue.org/ubuntu/10....7.5-1_amd64.deb](ftp://ftp.mondorescue.org/ubuntu/10....7.5-1_amd64.deb)
[*]wget [ftp://ftp.mondorescue.org/ubuntu/10....9.4-1_amd64.deb](ftp://ftp.mondorescue.org/ubuntu/10....9.4-1_amd64.deb)
[*]wget [ftp://ftp.mondorescue.org/ubuntu/10....7.3-1_amd64.deb](ftp://ftp.mondorescue.org/ubuntu/10....7.3-1_amd64.deb)
[*]dpkg -i mondo_2.2.9.4-1_amd64.deb mindi_2.0.7.5-1_amd64.deb mindi-busybox_1.7.3-1_amd64.deb
[/LIST]
[SIZE=2]Got instructions from [this ]("http://ubuntuforums.org/showthread.php?t=1485122")post and changed to amd64.
It all installed fine.
But when I try to do backup to cd or dvd it stops soon after starting.
The logs are here:
[COLOR=#000000][FONT=Arial]mindi.log [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_http://pastebin.com/PRnXuT8t_[/FONT][/COLOR]]("http://pastebin.com/PRnXuT8t")[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]mondoarchive.log [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_http://pastebin.com/JChVJspm _[/FONT][/COLOR]]("http://pastebin.com/JChVJspm")
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]

I have one harddrive with ubuntu on it and two that I use for files (ntfs) 
I just wont to backup the one with the operating system, to CD or DVD would be nice so if when I start really fiddling with it and break it i can just chuck in the cd and do a restor to get it back to exactly like it is now.

I am open to other apps if anyone knows of any that will do the job.
[/SIZE]

---

### Post by ubudog on 2011-02-19
You say you are open to other apps, so may I recommend Jungle Disk?  It's pretty awesome, here's some more info...

[http://www.jungledisk.com/](http://www.jungledisk.com/)

---

### Post by Red Kelly on 2011-02-19
> **ubudog said:**
> You say you are open to other apps, so may I recommend Jungle Disk?  It's pretty awesome, here's some more info...

[http://www.jungledisk.com/](http://www.jungledisk.com/)

Thanks but I should have clarified that a bit more, free (beer and freedom) and backup to a bootable CD or DVD.

Thanks anyway.

---

### Post by ubudog on 2011-02-19
Check out post #2 here.

[http://www.linuxquestions.org/questions/ubuntu-63/ghost-for-ubuntu-441797/](http://www.linuxquestions.org/questions/ubuntu-63/ghost-for-ubuntu-441797/)

That may be of more help.  :)

---

