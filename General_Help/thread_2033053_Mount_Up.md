---
title: "Mount Up"
date: 2012-07-25
forum: General Help
---

### Post by OldHarbottle on 2012-07-25
Hi,
   I've finally got round to replacing Windows 7 with Ubuntu 12.04 (Desktop) on my home media centre. The problem I am currently struggling with is how do I set up the windows shares for the two external usb hard disks.

so far I have samba server installed an working, with a visible share that I can see from a Window box. but when I try to open the share I get permission denied.

I spent the whole weekend with samba docs and think I have set up all the guest stuff correctly. My feeling is that the problem is the auto mount permissions on the hard disks (Holmes/Watson)

/media
drwx------ steven steven 4096 Jul 24 12:55 Holmes
drwx------ steven steven 4096 Jul 24 12:55 Watson

(both drives are formatted for NTFS)

How do set the default privileges to something more useful?

I know i could start messing about with fstab, but that seems kinda 'old school'


Regards
Steven

---

### Post by OldHarbottle on 2012-08-02
Got it all working, I decided to go fstab route after all.

---

