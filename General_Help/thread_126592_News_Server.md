---
title: "News Server"
date: 2006-02-06
forum: General Help
---

### Post by ockertom on 2006-02-06
Hi Peeps just wondering what would be a good imap, pop3, server to run handling 30 groups, yea only small so I wouldnt need a propietry server but one with security would be good, any links to setting up and maintainin would be appreciated :D Thanks in advance.

---

### Post by gsdefender on 2006-02-07
News server: Leafnode ([www.leafnode.org](www.leafnode.org))
POP3/IMAP server: Dovecot ([www.dovecot.org](www.dovecot.org))
SMTP server: The builtin Exim is more than enough.

Leafnode should already be in package repositories (maybe universe: I don't know since my server does not run Ubuntu actually); for Dovecot I recommend you to build the latest 1.0 beta from sources: I suspect Ubuntu includes the old stable version which has some known management troubles - I am not sure either.

For what concerns configuration, you'll find the files in /usr/doc/* very interesting and easy to understand. Try them, as I have been able to setup those programmes without any other help. And I'm not really a wizard when it comes to servers :-D.

---

