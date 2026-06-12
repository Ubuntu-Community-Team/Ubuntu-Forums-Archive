---
title: "any way to flush apt-get's database?"
date: 2009-08-03
forum: General Help
---

### Post by ricster on 2009-08-03
I've succesfully installed and configured fetchmail, dovecot and postfix so i can have my own mail server but despite the fact that it all works perfectly every time i do apt-get install for an unrelated package the below is output meaning i never get a clean exit.

again, let me stress, i manually configured it and it all runs perfectly i'd just like to stop apt/dpkg from doing this bey clearing it's brain out. How do i do that? i tried -f, clean and autoclean with no effect.

```
Setting up postfix (2.3.8-2+etch1) ...
setting synchronous mail queue updates: false
setting myorigin
setting destinations: $myhostname localhost.$mydomain localhost $mydomain
setting relayhost:
setting mynetworks: 127.0.0.0/8 192.168.1.0/24
setting mailbox_command
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: loopback-only
setting inet_protocols: ipv4
/etc/aliases does not exist, creating it.
/var/lib/dpkg/info/postfix.postinst: line 469: /etc/aliases: No such file or directory
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by unutbu on 2009-08-03
You seem to be missing /etc/aliases.

My /etc/aliases looks like this:
```

# /etc/aliases
mailer-daemon: postmaster
postmaster: root
nobody: root
hostmaster: root
usenet: root
news: root
webmaster: root
www: root
ftp: root
abuse: root
noc: root
security: root
root: USER
```

I assume the purpose of the file is to make mail sent to the users on the left to be forwarded to the user on the right of the colon (:). 

You might want to copy this file, changing USER to your username.
Otherwise, perhaps try making a dummy file:
```

sudo touch /etc/aliases
```

that might stop the postfix postinst script from complaining.

---

