---
title: "Home folder full of .mozilla_backup folders"
date: 2009-12-02
forum: General Help
---

### Post by DouglasCaixeta on 2009-12-02
Hi,

My home folder is strangely getting out of space. So I was checking and saw 3 folders:
.mozilla_backup_2009-11-02T20:43:28-0200
.mozilla_backup_2009-11-06T15:25:42-0200
.mozilla_backup_2009-11-20T10:55:49-0200

I never made any backup of Firefox. Each of this folders has around 1Gb. Can I delete this? What is creating this?

---

### Post by some-what-Gnu-2-networks on 2009-12-02
> **DouglasCaixeta said:**
> Hi,

My home folder is strangely getting out of space. So I was checking and saw 3 folders:
I never made any backup of Firefox. Each of this folders has around 1Gb. Can I delete this? What is creating this?


Cut the files to an external drive. If all works fine then, yes, delete them.

---

### Post by some-what-Gnu-2-networks on 2009-12-02
Are you sure that you haven't backed up thunderbird? it is also a mozilla program, and it is more likely that those backups belong to thunderbird.

---

### Post by DouglasCaixeta on 2009-12-02
Hi,

Thanks, I will try to move them.

No, I only use Firefox from Mozilla.

Perhaps is because I installed Firefox from Ubuntuzilla? Maybe they do backups?
But I'm sure I didn't request any of them.

---

### Post by lovinglinux on 2009-12-02
> **DouglasCaixeta said:**
> Hi,

Thanks, I will try to move them.

No, I only use Firefox from Mozilla.

Perhaps is because I installed Firefox from Ubuntuzilla? Maybe they do backups?
But I'm sure I didn't request any of them.

Yes, it does. Each time you install Ubuntuzilla, it makes an automatic backup of your mozilla folder. Anyway, you can safely delete those backups if you don't need them, but I would investigate why those backups are so big. I have a lot of add-ons installed, with big databases, but my .mozilla folder has only 360 Mb. Perhaps the Firefox cache was really big by the time of the backups. You could setup Firefox to delete stuff on exit, if you need to clear some space.

---

### Post by DouglasCaixeta on 2009-12-02
> **lovinglinux said:**
> [...]but I would investigate why those backups are so big. I have a lot of add-ons installed, with big databases, but my .mozilla folder has only 360 Mb. Perhaps the Firefox cache was really big by the time of the backups. You could setup Firefox to delete stuff on exit, if you need to clear some space.

It's big because I use Google Gears with Gmail offline. So, all my e-mails are in my home folder as well, all attachments.

---

