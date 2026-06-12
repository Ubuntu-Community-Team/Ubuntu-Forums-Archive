---
title: "Installing XP From USB, But Can't Format Right In Ubuntu"
date: 2009-09-14
forum: General Help
---

### Post by madprofessor on 2009-09-14
I do computer repairs so sometimes I need to reinstall XP. Sometimes people don't have the original Installation disk so I use my installation files with their product key. Here's my problem. I'm trying to get the installation files to boot from a flash drive, I know it's possible. I went into gparted and formatted the drive as ntfs, put the installation files on and changed the flag to boot. When I tried to boot from the flash drive I got a missing bootldr error. I did the same steps with Windows 7 and it booted. What am I missing or doing wrong?

---

### Post by shel-hall on 2009-09-14
Try using 'WinSetupFromUSB' to prepare and load the USB key with the XP installer image.  Googling for it will show you a download page with a completely incomprehensible write-up, and another page with a very good walkthrough on how to use it.

I've used it several times recently to install XP, and it works great.

-Shel

---

### Post by madprofessor on 2009-09-15
Thank You. It worked like a charm.

---

