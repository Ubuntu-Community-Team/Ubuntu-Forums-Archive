---
title: "URGENT HELP-windowsxp/ubuntu netbook DUAL BOOT-xp no longer boots from grub"
date: 2010-07-28
forum: General Help
---

### Post by Rhye on 2010-07-28
Well the title says all.

XP will no longer boot from the grub.

Instead it now says
#
Disk read error
Press Ctrl Alt + Del to restart
#

I have another thread about this but less detailed and we have currently found out on that thread:
-I can not boot from cd
-I have no access to another Windows machine
-I can only boot Ubuntu Netbook 10.0.4
-I have updated grub via terminal and it didn't change anything
-My \boot\grub\grub.cfg file is correct/fine

I do not know what to do this is the first time I have ever used or installed linux. I do however have an idea what I am doing but not with the problem I'm having.

Also -I CAN boot from USB

Thankyou for reading and all help is appreciated :)

---

### Post by worksofcraft on 2010-07-28
at command prompt:

sudo update-grub

it will find all your operating systems and update the boot menu for you even if you reconnected your hard drives differently.

.... so did it not find your windows XP and make a new menu entry?

---

### Post by Rhye on 2010-07-28
Yes I did this and it changed nothing.

I have no problem with seeing it. There is an option to boot to xp but when I do it it just says

Disk read error
Press ctrl alt del to restart

And that's it...

---

### Post by worksofcraft on 2010-07-28
OK

I suspect the problem is inconsistency between your BIOS settings and grub, but bioses are not standard so I can only tell you what I see on my computer:

When I boot my computer I press Del to enter the BIOS setup.

Look in "Standard CMOS setup" and note the drive order: On my computer it is

IDE Channel 0 Master WDC...
IDE Channel 0 Slave DVD...
IDE Channel 2 Master WDC...
IDE Channel 2 Slave WDC...

the WDC...'s are different hard drive identifiers from the manufacturer.

Now exit that and check in your "Advanced Bios Settings"
I have "Hard Disk Boot Priority - press Enter" so I press Enter and there I see these same drives.

Now this is the important bit: Make sure they are in the same order as in the standard setup, because that is the order that grub expects and that grub assigns the identifiers. If it is different then poor old grub will be trying to boot windows off the wrong drive!

so on my computer it says Channel 0 Master, then Channel 2 Master then Channel 2 Slave.

Note that the CD/DVD drive is not included becauseit is not a hard drive.

A bit further down is "First Boot Device" and I set that to DvD... of course if none is present then it moves on to second boot device which I set as "Hard Disk"

Check this out and tell us what you find on your system!

---

### Post by Rhye on 2010-07-28
Thanks I will try this tomorrow and let you know! :)

Be sure to check back in about 22-24 hours :)

---

### Post by Rhye on 2010-07-29
no that did not work, i only have one hard drive and it is just partitioned.

PLEASE COMMUNITY i need HELP

---

### Post by Rhye on 2010-07-29
Please Guys!!

[HTML]
<marquee>PLEASE HELP ME FIX MY ERROR THIS IS REALLY BAD</marquee>
[/HTML]

---

### Post by Rhye on 2010-07-29
Bump

---

### Post by Rhye on 2010-07-29
Omgcan someone help me!?!?!?!?!?

---

### Post by worksofcraft on 2010-07-29
Sadly I have no further ideas at the moment and you may have to start looking for disk tools that scan for defects:

Evidently grub install can read and identify your windows partition  but it may be that some critical data has got corrupted.

Could this be a deteriorating disk drive or has the machine suffered rough handling?

After booting to Ubuntu, in the 'Places' menu click on your windows partition to mount it and then you should be able to see all your files and things there.

Do make a backup of any critical data before trying anything else.

p.s. have look at your drive using
System->Administration->Disk Utility
also 
System->Administration->Storage Device Manager
and
Applications->Accessories->Disk Usage Analyzer
I don't know what to look for but it might give some kind of clue.
As for booting from CD, it is something your BIOS should be able to do regardless of what is on your hard drive and that's why I thought it was a problem with your bios settings to start with!

---

### Post by Stefanie on 2010-07-29
What did you do before things went wrong? Did XP boot correctly before, and when did it stop working? Did you change any settings?

Try this:

```
sudo aptitude install ntfsprogs ntfs-3g gparted
```

Now run gparted (partition editor) by selecting it from the settings > administration menu (or just press alt-f2 and run "gksudo gparted")

You will see an overview of your partitions. Right click your windows partition and select "check" to check the partition for errors (you might have to unmount it first). See if this fixes the problem.

---

### Post by Rhye on 2010-07-29
i pressed check and errors came up...

no it was fine until i installed linux which installed grub by itself

---

### Post by Rhye on 2010-07-29
errors attached..

---

### Post by Rhye on 2010-07-29
Bump

---

### Post by Rhye on 2010-07-29
BUMP. Please help people.

---

### Post by oldfred on 2010-07-29
Disk read error sounds more like a BIOS or hard drive error before you even get to grub or windows.
Run this to see if something looks wrong in your boot configuration, but it will not help if it is a drive problem.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

