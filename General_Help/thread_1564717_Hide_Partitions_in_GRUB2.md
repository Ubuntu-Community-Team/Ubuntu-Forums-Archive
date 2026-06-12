---
title: "Hide Partitions in GRUB2"
date: 2010-08-30
forum: General Help
---

### Post by [::AP::] on 2010-08-30
Greetings - 

I would like to hide two entries in my GRUB2...(to clean up a BURG theme)

Dell Utility Partition -on- /dev/sda1

Microsoft XP Embedded (Which I believe is Dell Media Direct) -on- /dev/sda5

I understand that you must edit it in either 'menu.lst' or '30-os-prober' files.

The entry is a little like this... (?)  

```
if [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi
if [ "${DEVICE}" = "/dev/sdXY" ]; then
continue
fi
```

I am not sure, however. 

I also do not understand what line to put it on? HELP!!!

Could someone please assist me with this? 
Please, do not give me this link:

'GRUB 2 Title Tweaks'
[http://ubuntuforums.org/showthread.php?t=1287602]("http://ubuntuforums.org/showthread.php?t=1287602")

...as it does not make much sense to me. I am new(ish) to Linux. 

Thank you,

[::AP::]

---

### Post by [::AP::] on 2010-08-31
Aw, c'mon. 15 views and no replies? :(

JK...

---

### Post by arpanaut on 2010-08-31
LOL!  Hey, Grub2 is as confusing to most of us as it is to you.
There are a few Grub 2 gurus around, hope one of them sees your post

In the meantime... TTT

P.S. It is frowned upon around here to bump posts more than once every 24 hours.

---

### Post by oldfred on 2010-08-31
drs305 likes to edit the scripts and I do a little of that. I just do the brute force copy the entries I want from grub.cfg into 40_custom, edit and turn off the os prober so I do not have duplicates.

Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

Some similar instructions, that are not quite as complex:
How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by [::AP::] on 2010-08-31
> **arpanaut said:**
> LOL!  Hey, Grub2 is as confusing to most of us as it is to you.
There are a few Grub 2 gurus around, hope one of them sees your post

OK - Thank you! *crosses fingers* Thanks for understanding..

> **arpanaut said:**
> P.S. It is frowned upon around here to bump posts more than once every 24 hours.

](*,) Oops, sorry. I am new to this forum, even forums in general. *must learn etiquette*

I understand why - it is annoying for a noob with a small aesthetic problem (like mine) to keep bumping their posts when others have a mega problem and need the most help (like computer is unbootable, hard drives wiped, etc)

Please excuse that...

Thanks,

[::AP::]

---

### Post by dino99 on 2010-08-31
some good readings below

---

