---
title: "dual boot XP and Ubuntu...floppy disk(s) fail (40)?!"
date: 2009-09-10
forum: General Help
---

### Post by moondy on 2009-09-10
Hi All,
(this is my 4th attempt at help on a forum, please break this curse!)

Here is the low down. I re-formatted my PC and figured that after installing XP i'd dual boot Ubuntu (9.04) (was very excited!)
So all went well, XP and Ubuntu installed as anticipated i could access both OS' for a couple of hours.

When i was in Ubuntu, i was trying to change my primary monitor (22") to have the toolbar instead of my 19".
I went on these forums to see what had to be done, and i needed to reboot for the changes to take effect.

After i rebooted, it didn’t list any of my 2 hard drives (150gb raptor, 1tb Samsung) or my Asus DVD/CD drive.

My motherboard (Nvidia 680I) stated 7F which only says in the manual as "Check POST error and display them and ask user intervention".
Well, the lovely post error comes up as:

```
floppy disk(s) fail (40)
```

Real helpful right? And considering i have NO floppy drive...(its a custom built PC)
And i have two options, F1 to continue and DEL for BIOS.

I checked BIOS first, reset to default, removed floppy drive from the boot menu, rebooted, same issue.

Hit F1 to continue now, and the only bootable option is the NVIDIA Boot Agent and it comes up with this:

```

NVIDIA BOOT AGENT 231.0528
PXE-E61: MEDIA TEST FAILURE, CHECK CABLE
PXE-M0F: EXITING NVIDIA BOOT AGENT

```

This goes on a continuous loop, failing every time. I've checked all cables and it all seems fine.
Now i cant even access my CD/DVD drive (completely disabled) which means i can’t even use a recovery disk or what have you. 
I am very doubtful its my hard drive...i leaning towards a /boot issue. But i don’t really know how i can even approach this.

Any other ideas?

Thank you in advance for your contribution.

---

### Post by moondy on 2009-09-10
Great, now its coming up with a 'fail to decode (001)'.

what has ubuntu done?!

---

### Post by P4man on 2009-09-10
This is not an ubuntu problem, this is a BIOS / hardware problem.

Nonetheless, I suspect either a cabling problem, or a IDE controller (which means motherboard) problem.

Some things you can try:

- Disconnect all drives except 1. Try booting with only the CDrom or only 1 drive connected (make sure its configured as master if you have PATA devices).

- Reset your bios. Check your motherboard manual, it usually involves shorting two pins and removing the battery for some minutes.

If none of this helps, I think you should prepare to RMA your motherboard.

---

### Post by chkneater on 2009-09-10
Yeah man, if it were any Ubuntu issue you would at least be able to access the boot menu and choose to boot Ubuntu or not. Even then you'd have the grub menu come up and you could safe boot.  I know this is redundant but check all cables, especially on the motherboard.  Also doubtful but possible, RAM chips come loose sometimes.

---

