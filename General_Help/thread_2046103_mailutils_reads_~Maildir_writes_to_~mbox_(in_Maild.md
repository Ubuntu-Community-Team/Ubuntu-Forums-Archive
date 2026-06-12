---
title: "mailutils reads ~/Maildir writes to ~/mbox (in Maildir format)"
date: 2012-08-22
forum: General Help
---

### Post by bazbar on 2012-08-22
I've searched around for hours now on how to solve this problem. The best answer I've seen so far indicates that maybe mailutils can't do what I want? That user switched to something he called "legacy mailx" ?

I'm very new to ubuntu.

I have ubuuntu 11.10 with:
mailutils/oneiric uptodate 1:2.2+dfsg1-3

I setup the pam.d settings according to this link: [http://ashtech.net/~dmarkle/blog/archives/162-Debian-5-Mailutils-and-Maildir.html](http://ashtech.net/~dmarkle/blog/archives/162-Debian-5-Mailutils-and-Maildir.html)

My $MAIL outputs: /home/-user-/Maildir

Dovecot and Postfix both work fine. But if I use "mail" to read the mail it moves the message from ~/Maildir to ~/mbox - mbox in this case is a directory with the same structure as the Maildir directory (not a flat file containing all the emails).

Does that make sense? It's as if mailutils knows that I want to use the Maildir format but somehow has the wrong directory name to write/save read mails - despite knowing where to get the unread mails.

Thanks for reading.

edit:

mailutils.rc reads as follows:
mailbox {
        mailbox-pattern "maildir:///home/${user}/Maildir";
        mailbox-type "maildir";
}

---

