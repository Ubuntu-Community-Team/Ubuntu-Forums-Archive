---
title: "PROFTPD: User Is Able To View Other Directories.."
date: 2012-07-07
forum: General Help
---

### Post by Didee on 2012-07-07
Hey,

Scenario is this:

I have a Webmin and ProFTPD setup (Debian)

Now, I am creating a user from "System" > "User and Groups".

I am specifying this user a directory in var/www/extuser

Now, when I connect through FTP, this user is able to see var/www and the whole server. 

How do I limit it to his directory only.

Thanks

---

### Post by Rexilion on 2012-07-08
I'm by no means an ftp, proftp or server expert. But looking at the proftpd.conf homepage I saw some examples. I see directives like this:

<Limit CWD XCWD CDUP>
	DenyAll
</Limit>

I think that especially 'CDUP' is what you are looking for. But be carefull, it's quite possible that you might overlook some escape routes!

---

