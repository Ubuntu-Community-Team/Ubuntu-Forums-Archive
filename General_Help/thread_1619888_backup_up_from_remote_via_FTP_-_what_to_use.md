---
title: "backup up from remote via FTP - what to use?"
date: 2010-11-12
forum: General Help
---

### Post by Ascenti0n on 2010-11-12
Hi all, I have a website hosted remotely that I want to backup regularly. It's a Drupal site and I know to backup the database, but I need advice on backing up the files, particularly the 'sites' folder.

I have access via **FTP**, and need a tool that I can run from a** bash script** (and using cron) and will do **incremental backups**. I know **Rsync** can do this, but I read on other posts that **Rsync cant work over FTP?** What other tools are available that will do what I need?

---

### Post by lmarmisa on 2010-11-12
Try to use Filezilla client.

[http://www.thinkdave.com/how-to-backup-your-website-using-filezilla-ftp/](http://www.thinkdave.com/how-to-backup-your-website-using-filezilla-ftp/)

---

### Post by Ascenti0n on 2010-11-12
> **lmarmisa said:**
> Try to use Filezilla client.

[http://www.thinkdave.com/how-to-backup-your-website-using-filezilla-ftp/](http://www.thinkdave.com/how-to-backup-your-website-using-filezilla-ftp/)

does it do command line incremental backups?

---

