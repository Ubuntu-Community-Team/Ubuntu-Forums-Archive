---
title: "Do I need port 5900 open for VNC if I tunnel it through SSH?"
date: 2011-07-15
forum: General Help
---

### Post by s3a on 2011-07-15
Apart from the security benefits, does using VNC as an SSH tunnel mean I only need to have SSH's port 22 open?

Any input would be appreciated!
Thanks!

---

### Post by bodhi.zazen on 2011-07-15
VNC is insecure as the traffic is not encrypted, including the log in password.

Tunneling over ssh encrypts the traffic, including the password, and is thus more secure.

No you forward port 22 only , and not 5900.

See: [http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Also, IMO, FreeNX is a better option, very fast and secure.

If you can, better to use ssh -X or learn the command line.

---

