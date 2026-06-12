---
title: "Can someone explain this?"
date: 2006-03-17
forum: General Help
---

### Post by GarethMB on 2006-03-17
Why have i only saved 4 GB data but have used up nearly 8GB of this partition on my HDD?

---

### Post by aysiu on 2006-03-17
I don't see why it's so confusing.

Both hda3 properties and disks manager say you have 28.8 GB free.

The hda3 properties says 702 items, totalling 3.6 GB **(some contents unreadable)**.

My guess is that the unreadable content is 4.38 GB.

---

### Post by FizDev on 2006-03-17
Could you post the output of "df"?

---

### Post by GarethMB on 2006-03-17
[QUOTE=FizDev]Could you post the output of "df"?[/QUOTE]
gareth@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1              9614116   4387900   4737844  49% /
tmpfs                   502064         0    502064   0% /dev/shm
tmpfs                   502064     12588    489476   3% /lib/modules/2.6.12-10-386/volatile
/dev/hda3             37982596   3949896  32103296  11% /media/hda3
gareth@ubuntu:~$

---

### Post by Ivan Matveich on 2006-03-17
sudo find / -type f -printf "%k %f\n" | sort -n

That'll list your files sorted by kilobytes size---maybe you have some big useless files hanging around?

---

### Post by aysiu on 2006-03-17
```
df -h
``` may make it easier to read.

---

### Post by GarethMB on 2006-03-17
Is there a way to browse a folder and see undreadable files?

---

### Post by GarethMB on 2006-03-17
Right this all makes sense now, i've seen these hidden files. But what worries me is that a lot of them were in folders called .trash. I've deleted the contents of these. But i have a final question. Will ubuntu periodically clean up these files or will my disc usage continue to soar? As programs, archives etc. i've deleted are hidden away from me. 

-Is there a command that deletes all unnecessary files or something?

---

### Post by dcstar on 2006-03-17
[QUOTE=GarethMB]Right this all makes sense now, i've seen these hidden files. But what worries me is that a lot of them were in folders called .trash. I've deleted the contents of these. But i have a final question. Will ubuntu periodically clean up these files or will my disc usage continue to soar? As programs, archives etc. i've deleted are hidden away from me.

-Is there a command that deletes all unnecessary files or something?[/QUOTE]
Just empty the trash occasionally , that is where your "deleted" files go.

If you want to permanently delete files:

System-Preferences-File Management

has an option to "Include a Delete Command that bypasses Trash"

---

### Post by new2linux2009 on 2006-03-17
just so you know 10/3/2006 hasn't happened yet

---

### Post by taurus on 2006-03-17
[QUOTE=new2linux2009]just so you know 10/3/2006 hasn't happened yet[/QUOTE]
#-o 

Or I assume he means March 10th, 2006 (from looking at the date when he joined the forum)!!!

---

### Post by GarethMB on 2006-03-18
Yes it has 10th March 2006. That was 8 days ago.

---

### Post by steve.horsley on 2006-03-18
[QUOTE=new2linux2009]just so you know 10/3/2006 hasn't happened yet[/QUOTE]
By my reckoning, it happened 8 days ago.

---

### Post by aysiu on 2006-03-18
American dates are backwards: month/date/year
Everyone else in the world: date/month/year

---

### Post by Ramses de Norre on 2006-03-18
the tenth day of the third month I think he means. Dates are written like that in Europe.

EDIT: many figured this out while I was typing:)

---

