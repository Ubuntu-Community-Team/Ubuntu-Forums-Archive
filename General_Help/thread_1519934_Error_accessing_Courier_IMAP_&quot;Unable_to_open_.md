---
title: "Error accessing Courier IMAP: &quot;Unable to open this mailbox&quot;"
date: 2010-06-28
forum: General Help
---

### Post by efalk on 2010-06-28
Hi all; I found this issue in the archives, but not the solution I was looking for.

Background: Ubuntu 8.04.  I installed courier imap and configured it to search for email in the individual users' ~/Mail directory.  It worked just fine for several years.

Today, while trying to update my SSL certificate I reinstalled courier imap.

Either I corrupted my config files, or the new version is sufficiently different from the old version that something is broken.  Now, when I try to connect to my imap server, I get this message:

> The current command did not succeed.  The mail server reposnded: Unable to open this mailbox..

Any way out of this mess?  I'm locked out of my email until I solve it.

---

### Post by efalk on 2010-06-28
I should also add: if I set "MAILDIRPATH=Maildir" (the default) in the config files, attempting to open a mail folder fails silently (from the user's point of view) but shows "chdir Maildir: No such file or directory" in /var/log/mail.info.

If I set "MAILDIRPATH=Mail", where the mail folder actually is, I the user gets "Unable to open this mailbox" while nothing is written to the log files.

This using Thunderbird.  I also tried Evolution with similar results.

---

