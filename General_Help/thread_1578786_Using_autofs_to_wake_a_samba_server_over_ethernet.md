---
title: "Using autofs to wake a samba server over ethernet"
date: 2010-09-20
forum: General Help
---

### Post by powerpleb on 2010-09-20
Hello all,

I'm trying to set autofs up to wake a samba file server whenever I want to use it. I found [this page]("http://tech-bodges.blogspot.com/2010/06/linux-autofs-and-wake-on-lan-bodge.html") which apparently demonstrates how to do it with NFS. With a bit of modification I've managed to come up with this:


```

/etc/auto.wake

#!/bin/sh
hostsrv=<server ip address>
hostmac=<server mac address>
opts="-fstype=cifs,rw,credentials=/etc/samba/.creds"

netcat -w 5 -z $hostsrv 445
status=$?

if [ $status -ne 0 ]
then
   /usr/sbin/etherwake -i $hostsrv $hostmac
   sleep 60
fi

/bin/echo -n "share"
/bin/echo -n -e "\t"
/bin/echo -n "$opts"
/bin/echo -n -e "\t"
/bin/echo "://$hostsrv/share"
```

Now, I've added this line to auto.master 
```
/server /etc/auto.wake --timeout=60 --ghost
```

and restarted autofs
```
sudo service autofs restart
```

It wakes up the server successfully but then when I wait 60 seconds and browse the /server directory on the client the share doesn't appear at all.

Any help figuring out why it isn't working would be appreciated.

---

### Post by powerpleb on 2010-09-26
:-k

---

