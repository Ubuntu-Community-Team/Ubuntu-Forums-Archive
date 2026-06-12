---
title: "BackUp Question"
date: 2010-07-13
forum: General Help
---

### Post by joek71 on 2010-07-13
Hello

I am running the latest version of Ubuntu and I have a file that is shared in the office that everyone drops there files in there daily.  How can I backup these daily files to my usb automatically?

Thank you.

---

### Post by mike555 on 2010-07-13
I use "LuckyBackup" because it is easy ... but I also use "DropBox " , just in case..........

---

### Post by joek71 on 2010-07-13
lucky backup? is that something i can install or is it the cloud?
I have a usb connected to this machine and wanted all info to be saved to the usb.
Does ubuntu have something like an app that can make auto backups?

---

### Post by mike555 on 2010-07-13
LuckyBackup is in package manager and can be set to backup daily or at a set time ........

---

### Post by sgosnell on 2010-07-13
Set up a cron job using rsync.  Cron jobs can be set to run at any frequency, on any days, weeks, or months you like.  Rsync will back up any files, directories, drives, etc that you tell it to, to any drive/folder you want.  There are lots of threads here on both cron jobs and rsync, plus the wiki and Google will give you lots of reading.

---

### Post by joek71 on 2010-07-13
Thank you guys, you are the best.

Thank you

---

