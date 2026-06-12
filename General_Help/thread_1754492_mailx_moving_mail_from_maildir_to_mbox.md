---
title: "mailx moving mail from maildir to mbox"
date: 2011-05-10
forum: General Help
---

### Post by Rigrig on 2011-05-10
I'm having kind of a weird problem: mailx moves read messages from my maildir to an mbox file.

My ISP only provides POP3 access, so I've set up getmail to automatically download messages into my local maildir (~/.mail), and then I access them from evolution using IMAP+(local running)dovecot. This all works fine.

The problem arises when I access my mail from the command line (usually because it tells me I have new mail when I ssh in):

mailx properly shows new messages from ~/.mail, but after reading them it moves them to ~/mbox, while displaying something like```
Saved 1 message in /home/richard/mbox
Held 0 messages in /home/richard/.mail
```
After this the messages are indeed in the ~/.mbox file, and gone from the maildir (Dovecot won't show them, and I looked for them manually in ~/.mail/cur and ~/.mail/new)

I've setup /etc/pam.d/sshd and /etc/pam.d/login to have the line ```
session    optional     pam_mail.so dir=~/.mail standard
```
echo $MAIL displays '/home/richard/.mail'
/usr/bin/mail symlinks to /etc/alternatives/mail which symlinks to /usr/bin/mail.mailutils

Any ideas on how to fix this would be much appreciated.

Edit: Kinda solved it by installing heirloom-mailx instead of mailutils. Looks like there's no way to have mailutils save back to my maildir.

---

