---
title: "compromised system...please help"
date: 2011-03-07
forum: General Help
---

### Post by vivek.pandey on 2011-03-07
hi everyone
     i was trying to download using wget and i get following problem

vivek@NEO:~$ wget [https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz](https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz) -O /tmp/Macbuntu-10.10.tar.gz
Error parsing proxy URL [http://localhost:4001](http://localhost:4001) : Bad port number.

i tried this

vivek@NEO:~$ set | grep -i proxy
HTTP_PROXY='http://localhost:4001 '
http_proxy='http://localhost:4001 '
-find -s -nice -nouserlib -noclasspath -autoproxy -main' -- "$cur" ));
PreferredAuthentications Protocol ProxyCommand PubkeyAuthentication \
vivek@NEO:~$

i tried even this 
sudo apt-get purge anon-proxy
but after this i run wget
and get same error

i dont have  any such proxy programs like onion or squid running or even installed  but i guess i have tor running which i installed lomg back... 
someone suggested me to post it as a thread named compromised system.
so   anyone please help
thanx to all in advance

---

### Post by Habitual on 2011-03-07
Here's the real link.
```
wget [http://superb-sea2.dl.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz](http://superb-sea2.dl.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz)
```[]("http://superb-sea2.dl.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz")

---

### Post by vivek.pandey on 2011-03-07
> **Habitual said:**
> Here's the real link.
```
wget [http://superb-sea2.dl.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz](http://superb-sea2.dl.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz)
```[]("http://superb-sea2.dl.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz")

thanx for your reply
i get this
vivek@NEO:~$ wget [http://superb-sea2.dl.sourceforge.ne...u-10.10.tar.gz](http://superb-sea2.dl.sourceforge.ne...u-10.10.tar.gz)
--2011-03-08 00:24:21--  [http://superb-sea2.dl.sourceforge.ne...u-10.10.tar.gz/](http://superb-sea2.dl.sourceforge.ne...u-10.10.tar.gz/)
Resolving superb-sea2.dl.sourceforge.ne...u-10.10.tar.gz... failed: Name or service not known.
wget: unable to resolve host address `superb-sea2.dl.sourceforge.ne...u-10.10.tar.gz'
vivek@NEO:~$

---

### Post by Habitual on 2011-03-07
must be the board parsing long strings...

"wget http://superb-sea2.dl.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz"

or see x.txt attached.

---

### Post by vivek.pandey on 2011-03-07
must be the board parsing long strings...

"wget http://superb-sea2.dl.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz"

thanx for the link its working but donno how even the url that i had iniatialy is working...my question still remains was i hacked or something... i mean how that 4001 error is gone now without any effort

---

### Post by Habitual on 2011-03-07
My best guess is that the message "Error parsing proxy URL [http://localhost:4001]("http://localhost:4001/") : Bad port number." was an error at sourceforge redirecting your request to another server (superb-sea2.dl.sourceforge.net) via a proxy they run.

```
telnet localhost 4001
```if your system "answers" then you have issues and may be compromised, else, relax.

let us know...

---

### Post by vivek.pandey on 2011-03-07
> **Habitual said:**
> My best guess is that the message "Error parsing proxy URL [http://localhost:4001]("http://localhost:4001/") : Bad port number." was an error at sourceforge redirecting your request to another server (superb-sea2.dl.sourceforge.net) via a proxy they run.

```
telnet localhost 4001
```if your system "answers" then you have issues and may be compromised, else, relax.

let us know...

telnetting gave me this

vivek@NEO:~$ telnet localhost:4001
telnet: could not resolve localhost:4001/telnet: Name or service not known

---

### Post by Habitual on 2011-03-07
You're good then. :)

Does my explanation of the "error" make sense to you?

---

