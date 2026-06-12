---
title: "Web Dev Setup"
date: 2009-10-09
forum: General Help
---

### Post by sjemms on 2009-10-09
Hi guys

I'm a PHP Developer and wish to set up Ubuntu 9.04 Server edition as an internal web development machine.

I've used the How To Forge's guide, but it doesn't really satisfy our needs ([http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3) if you need the link).

The problem is revolving around the DNS settings (I've tried both MyDNS and BIND9).

I'd like it so that everyone on our LAN can access every project on the site like this....

[http://[PROJECT_NAME]](http://[PROJECT_NAME]).[USER_NAME].dev

I used to work at a place that had the setup like that, so I know it's possible and it was very handy for us to collaborate on projects.  I know that before we had to force the client computers to check that server's DNS server.

I've got the web server working on [http://dev](http://dev), but that's only because Samba is doing it.

We don't need FTP as we use Samba.

Thanks

Si

---

