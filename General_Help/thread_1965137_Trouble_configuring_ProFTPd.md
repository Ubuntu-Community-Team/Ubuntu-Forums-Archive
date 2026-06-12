---
title: "Trouble configuring ProFTPd"
date: 2012-04-25
forum: General Help
---

### Post by d4wntracker on 2012-04-25
I'm using ProFTPd as my ftp-server daemon. And I'm running Ubuntu Server 11.10, no GUI. And I'm having a lot of trouble configuring the daemon so it will function the way I wish.

I'm using this directory structure:
/var/shares/pub/
/var/shares/priv/
/var/www/

I wish to have 2 users that can use the FTP service.
1. dennis
-> has full access to /var/shares/ (+ the 2 directories in it)
-> has full access to /var/www/

2. www
-> has limited access to /var/www/ (STOR, RETR, MKD, LIST)

The anonymous account has been disabled. That's the one thing I got working.

Currently the last bit (after the default anonymous settings) of my proftpd.conf file looks like this:
```

# ----------------------- user account
<Limit LOGIN>
AllowUser dennis
DenyAll
</Limit>

<Anonymous /var/shares>
   User dennis
   Group nogroup

   <Limit ALL>
     AllowAll
   </Limit>
</Anonymous>

```

When the user "dennis" connects it is transfered to the /var/shares/pub/ directory, and not /var/shares/

What am I forgetting?

---

### Post by d4wntracker on 2012-04-25
** Self-Reply **

Managed to figure out what I did wrong.
Got it working by correctly entering the right directories.

---

