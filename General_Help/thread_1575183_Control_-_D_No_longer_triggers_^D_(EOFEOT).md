---
title: "Control - D No longer triggers ^D (EOF/EOT)"
date: 2010-09-15
forum: General Help
---

### Post by Takaian on 2010-09-15
Recently, I have been trying to get nagios to send email alerts. I found out my problem was in the actual mailing process, using either /usr/bin/mail, sendmail, or mailx. I tested a few things and sendmail seemed to be working the best, but I realized I had no /etc/mail/ folder to change my options. So I did a quick apt-get install sendmail and it successfully installed. After that, I was able to edit my mail server, etc, in the config. The problem is that after I updated sendmail, Control D no longer works at all. After typing in my email message (on all 3 commands) I try to do a ^D trigger, and it just does nothing. EVERY other ^ letter works, just not the one I need (EOF/EOT). Any suggestions as to how to get this functionality back?

---

### Post by psusi on 2010-09-15
Check stty, or just enter a line with only a period on it and that will also get mail to stop reading and send.

---

### Post by Takaian on 2010-09-15
It seems that my stty is correct, but now I used a single period to trigger EOF, and it worked, but I had to wait roughly a minute before it completed the EOF and brought me back into my shell prompt. Is this to be expected or is something still wrong? The mail still doesn't seem to be going through.

---

