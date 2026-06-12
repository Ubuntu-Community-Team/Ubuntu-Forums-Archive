---
title: "Setting up hotwayd and xinetd"
date: 2006-03-05
forum: General Help
---

### Post by Asrael on 2006-03-05
I've been trying to set up hotwayd to be able to read mail in evolution from my lycos account.

I have installed hotwayd. However Telnet says the following:
telnet 127.0.0.1 110
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

I suspect the problem is the xinetd.conf file, although I'm not sure.
My entire xinetd.conf file:
# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/


service hotwayd
{
#only_from=192.168.0.0/24 #for gentoo security?
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = nobody
groups = yes
server = /usr/local/sbin/hotwayd
server_args = -p [http://proxy:8080](http://proxy:8080) -u proxy_user -q
proxy_password
port = 110
}

Any thoughts?

Thanks

---

### Post by dpm on 2006-11-04
In my particular case it helped to add the line

```
hotwayd: 127.0.0.1
```

to **/etc/hosts.allow**

---

