---
title: "[ERROR]Ubuntu installation"
date: 2012-01-13
forum: General Help
---

### Post by jairoh_ on 2012-01-13
i want to change my os to ubuntu. so here's what i did...

- Boot from the flash disk, select "**Command Line Install**" option
    [b]EDD: Error 0100 reading sector 1
    EDD: Error 0100 reading sector 2
    EDD: Error 0100 reading sector 3
                                        to
    ""       ""      ""       ""        ""    thousands[/b]
- Select a language: **English **
- Select your location: **United States **
- Detect keyboard layout: **No **
- Configure the keyboard: **USA **
- Configure the keyboard layout: **USA** 
- Configure the network hardware with DHCP: **Successful**
- Configure the network hostname: **Ubuntu** 
- Choose a mirror of the Ubuntu archive: **United States** 
- Ubuntu archive mirror: **us.archive.ubuntu.com **
- HTTP proxy information: **Blank **then i press **Continue**


and then appeared
> 
             Bad Archive Mirror
An error has been detected while trying to use the specified Ubuntu archive mirror.


Possible reasons for the error are: incorrect mirror specified; mirror is not available (possibly due to an unreliable network connection); mirror is broken(for example because an invalid release was found); mirror does not support the correct Ubuntu version.


Additional details may be available in /var/log/syslog or virtual console 4.


Please check the specified mirror or try a different one.


so i changed the mirror, but still that error appears(the one inside the quote). any suggestions? TIA! :(

---

### Post by Rubi1200 on 2012-01-13
Hi and welcome to the forums :-)

What version of Ubuntu are you trying to install?

---

### Post by jairoh_ on 2012-01-13
11.10 sir 32bit. maybe it's just corrupted, so i'm downloading it again. i don't want to use windows anymore, i want to replace it w/ ubuntu so bad. is it advisable to use "command-line install"? or just "install?"

---

### Post by Rubi1200 on 2012-01-14
It's quite possible the ISO was corrupted or perhaps you need to burn at a lower speed.

If you want to replace Windows completely and just use Ubuntu then choosing to install is probably the easiest method unless there is a specific reason to do a command-line install (e.g. you have a RAID setup, LVM, or similar).

---

### Post by 2F4U on 2012-01-14
How did you put Ubuntu on the flash disk? It looks to me as if that process failed and now the boot image is corrupted.

---

