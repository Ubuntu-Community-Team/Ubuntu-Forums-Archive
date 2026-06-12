---
title: "Ubuntu keeps restarting?"
date: 2011-05-21
forum: General Help
---

### Post by Piccolo48 on 2011-05-21
Hello

As soon as updating my version of Ubuntu; Ubuntu will periodically restart/reboot.  What is causing this?  How do I stop this?

---

### Post by linuxinstalledfromhdd on 2011-05-21
Rollback to 10.10 for now. See if it happens again.  If it happens again you have a power supply failure that is immanent or cpu is overheating.  Check bios to see what you have your cpy temp at, and how everything looks temp-wise.

---

### Post by Piccolo48 on 2011-05-21
Ok...when you say "rollback"...is that easy to do?  Or am I going to have to delete and reinstall ubuntu all over again?

---

### Post by linuxinstalledfromhdd on 2011-05-21
You don't have to do much. Just create a USB live stick of Ubuntu 10.10.  You can research that on google.  Don't change anything just yet.  Boot from that USB device and leave it on for some time, and make observations of how it might react differently to rolling it back. See if it makes any kind of real defining difference.

---

### Post by Piccolo48 on 2011-05-21
Alright, thanks I'll try that.......................

---

### Post by dFlyer on 2011-05-21
> **Piccolo48 said:**
> Hello

As soon as updating my version of Ubuntu; Ubuntu will periodically restart/reboot.  What is causing this?  How do I stop this?

First what version of ubuntu are you running? I can't guess what is causing this, nor can I tell you how to fix it without knowing what version your running.

---

### Post by linuxinstalledfromhdd on 2011-05-21
they upgraded to the latest version it appears, and it is causing it to restart after while. It could be anything at this point, true.

---

### Post by Piccolo48 on 2011-05-21
Ok, I typed lsb_release-a in to Terminal:

I think the release is 11.4 codename Natty


Although, when I select it from the partition it says:  2.6.38-8

---

### Post by c_winwood on 2011-06-13
I have also been having this issue.

My laptop is 2 months old and was set up as a dual boot with windows 7 and Natty.  This rebooting issue is a more recent occurrence only happening in the last 2 weeks.  Its not a power issue, like I said, new laptop and also there are some lines of text that flash up before it returns to the login screen.  Perhaps a reboot isn't really the right terminology, its more a case of natty returning you to the log in screen.  As this is a more recent occurrence and I haven't been tinkering with anything I would have to assume it was down to one of the updates.

At the end of the day this new ubuntu is great. Its still in the Beta stage I believe so I was expecting quite a few issues.  This is the only one Ive had.  In fact I think this has probably been the least problematic Ubuntu ever.

---

