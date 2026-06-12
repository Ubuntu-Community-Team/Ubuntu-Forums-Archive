---
title: "[Ubuntu 10.04] Can't connect to web server on non-80"
date: 2010-07-16
forum: General Help
---

### Post by littlebigman on 2010-07-16
Hello

I'm having the same issue when using different browsers on the same client, and even trying from a different client: A web server running on Ubuntu works fine when listening to requests on TCP80 but is not reachable when configured to listen on eg. TCP8787:

```

# netstat -nat
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp6       0      0 :::8787                 :::*                    LISTEN     

```

I have the same issue when using Nginx or Cherokee, so I suspect there's something in Ubuntu that triggers this.

Has someone seen this and knows what to do?

Thank you for any hint.

---

### Post by gmargo on 2010-07-16
It's either a firewall issue or an external router issue, or you haven't specified the address correctly.  What do you get when you test with telnet?  (i.e. "telnet hostname 80" vs "telnet hostname 8787")?

---

