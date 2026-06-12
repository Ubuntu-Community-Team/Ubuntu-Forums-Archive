---
title: "How Do I chkdsk /r on Ubuntu Computers?"
date: 2011-01-27
forum: General Help
---

### Post by LonelyAspie on 2011-01-27
Yesterday, by Dad's computer crashed (running WInows XP), I had to hook up the HDD as an external to my Mom's computer (also running Windows XP) do chkdsk (check disk) /r (repair) in comand promt (entering cmd in the start menu).

How do I do that on ubuntu. I know how to get to the terminal, Ubuntu quick start menu (AAlt+F2). Just wondering, because my main OS is Ubuntu and I also have it on my Mom's computer now, for the time being.

---

### Post by coffee412 on 2011-01-27
> **LonelyAspie said:**
> Yesterday, by Dad's computer crashed (running WInows XP), I had to hook up the HDD as an external to my Mom's computer (also running Windows XP) do chkdsk (check disk) /r (repair) in comand promt (entering cmd in the start menu).

How do I do that on ubuntu. I know how to get to the terminal, Ubuntu quick start menu (AAlt+F2). Just wondering, because my main OS is Ubuntu and I also have it on my Mom's computer now, for the time being.

fsck is your command. There are some switches also for it but the main command line is:

fsck /dev/sd*

Star is whatever drive you are checking.

for more info on fsck just type in "man fsck" in a term window and it will show you.

---

### Post by LonelyAspie on 2011-01-27
Thanks, how to you know to drive letter? Is it, for axmaple, main drive is sdc1, 2nd drive is sdb2?

Also, also, how to you put letters in, like -f or -a?

---

### Post by coffeecat on 2011-01-27
You cannot run chkdsk on Ubuntu. Microsoft's chkdsk is a utility to repair Microsoft filesystems that only runs in Windows. Linux filesystem utilities are for repairing Linux filesystems. There is a terminal  app called ntfsfix but...

[quote="man ntfsfix"] ntfsfix  is a utility that fixes some common NTFS  problems.  ntfsfix is NOT a Linux version of chkdsk.  It only repairs  some  fundamental  NTFS inconsistencies,  resets  the  NTFS  journal  file and schedules an NTFS consistency check for the first boot into  Windows.[/quote]

If you have a NTFS filesystem that needs repairing, you need Windows and chkdsk - there is no getting away from that. If you do not have access to a running Windows system and have a Windows installation disc (it needs to be a Microsoft one, not a manufacturer's restore disc) then you can use the repair console command prompt instead.

---

### Post by Habitual on 2011-01-27
> **LonelyAspie said:**
> ...How do I do that on ubuntu...
```

sudo shutdown -rF now
```
or
```
sudo touch /forcefsck
```
and reboot.

---

### Post by tlotr on 2013-02-12
Hi,

I just tried the ntfsfix command in the terminal and it worked for me.

ntfsfix -b /dev/sdc1

Thanks coffeecat for this command.

Everytime the Ubuntu was unable to mount my ntfs drive I had to boot from the cd and then run the chkdsk command but now I think I dont have to do that any more. Thank you once again.

---

