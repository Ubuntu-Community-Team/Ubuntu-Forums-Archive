---
title: "Libre Office Calc will not open .XLS file"
date: 2012-07-09
forum: General Help
---

### Post by kwalters on 2012-07-09
Libre Office calc problem

I run Ubuntu 11.10 64 bit on an AMD dual core processor.  I dual boot with Windows XP as well

I track my investments in a spreadsheet in Excel .XLS format so that I can open it from either operating system.
This has worked successfully for several years.  If I open it in Windows it uses Microsoft Excel; if I open it in Ubuntu, it comes up in Libre Office Calc.  In earlier Ubuntu versions, Open Office was the Ubuntu software that opened it.


All of a sudden, I cannot open it in Ubuntu.  Libre Office Calc comes up with a message that this spreadsheet is locked for editing by an unknown user.  It will only let me open it read only

Windows still opens it normally with no mention of anything being locked for editing. I have tried everything I can think of to look (in Ubuntu and Windows) for anything telling me the spreadsheet is locked for editing; in the hopes that I could then unlock it.  But I am clean out of ideas.

Anyone out there got any?

KW

---

### Post by steeldriver on 2012-07-09
what filesystem is the xls file on? is it remote or local?

---

### Post by jmfal on 2012-07-09
This may help 

[http://office.microsoft.com/en-us/excel-help/lock-or-unlock-specific-areas-of-a-protected-worksheet-HA010096837.aspx](http://office.microsoft.com/en-us/excel-help/lock-or-unlock-specific-areas-of-a-protected-worksheet-HA010096837.aspx)

---

### Post by kwalters on 2012-07-10
> **steeldriver said:**
> what filesystem is the xls file on? is it remote or local?

It is on my NAS hard drive (is that remote?) which is formatted NTFS

KW

---

### Post by LewisTM on 2012-07-10
You probably have a .~lock.filename.ext file hidden in your directory, that should have been deleted but wasn't because of an interruption.
Close Libre, open a file manager and reveal the hidden files in your folder. Delete any .~lock file and you should be good to go.

Cheers!

---

