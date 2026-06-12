---
title: "dovecot-postfix sql authentication problem"
date: 2009-12-21
forum: General Help
---

### Post by semi-newbie on 2009-12-21
Hello,

I am attempting to get dovecot-postfix to work against an SQL-based virtual mail setup (pam is disabled).  I see text in /var/log/mail.err such as

dovecot: auth-worker(default): sql(user.name,the.ip.add.ress): Password query failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROM mailbox WHERE local_part = 'user.name' AND domain = '' AND active = 1' at line 1

I believe this is because MySQL is choking on the missing domain name, which should have been substituted in for %d, but nothing appeared there instead, even though user.name substituted for %n just fine.

[http://wiki.dovecot.org/DomainLost](http://wiki.dovecot.org/DomainLost) indicates a couple of different reasons this might happen to me, but these do not apply in my case.  I don't have auth_username_format set at all, and my password query looks as follows:

password_query = \
    SELECT local_part as username, \
        domain, \
        password, \
        '/srv/virtmail/%d/%n' as userdb_home, \
        '/srv/virtmail/%d/%n' as userdb_mail, \
        150 as userdb_uid,
        150 as userdb_gid,
    FROM mailbox WHERE local_part = '%n' AND domain = '%d' AND active = 1

where UID 150 = virtmail user and GID 150 = virtmail group.

In the userdb_home and userdb_mail, also the %d gets substituted by nothing, so it ends up as '/srv/virtmail//user.name' instead of '/srv/virtmail/domain.name/user.name'.

I simply cannot figure out the reason why %d does not convert into the proper domain string, so I cannot correct the problem.

I do have the file /etc/mailname set to hold the single line

domain.name

(using the real domain name, of course, and with a carriage return after it).

Does anyone know of additional reasons that dovecot's %d substitution would fail?

---

### Post by semi-newbie on 2009-12-26
Forcing the mail user agent client that is connecting via SMTP (on 587) to specify the @domain.name portion of their email address solves this problem.

---

### Post by luserbackslashunderscore on 2012-04-25
would you mind explaining how ?

i have this same problem but this is not a very elegant solution, i.e. what happens if its a client who cant do that, dovecot should be sorting this out not the client...
what do you reckon ?

---

### Post by Siltaar on 2013-01-23
Got the same problem.

Fixed it the same way.

---

### Post by Siltaar on 2013-01-23
Ok, joking…

The trick is that I was testing my dovecot authentication mechanism using mutt, via the syntax : mutt -f imap://user@mail.server.fr

But this way mutt is only sending 'user' to dovecot, and so %d can't be splitted appart from the recieved userid.

Using syntax mutt -f imap://user@wanted.domain@mail.server.fr may seems ugly, but it allows mutt to send 'user@wanted.domain' to dovecot and this last one succeed in splitting it into %u -> 'user' and %d -> 'wanted.domain'.

So my %d was empty just because my client wasn't giving something for it to be expended to.

---

