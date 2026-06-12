---
title: "cant log into ad with likewise-open"
date: 2011-02-16
forum: General Help
---

### Post by phun-ky on 2011-02-16
EDIT: Solved it.

I'm trying to get my client to talk to the AD controller we have. See info under. Will update issue continously with input.

Reinstalled Ubuntu 10.10 64 bit
installed likewise-open

<user>@ai-328:~$ sudo domainjoin-cli join <domain> <adminuser>
[sudo] password for <user>: 
Joining to AD Domain:   <domain>
With Computer DNS Name: <hostname>.<domain>

<adminuser>@<domain>'s password: 

Error: Lsass Error [code 0x00080047]

1225 (0x4C9) ERROR_CONNECTION_REFUSED - Unknown error


open ldap version: 2.4.23-0ubuntu3.4

When I do some lw commands i get the domain information as if i was connected (maybe i am), but i still get this error..

Getting this aswell when i try to leave the domain

Error code: CENTERROR_DOMAINJOIN_LSASS_ERROR (0x00080047)

Backtrace:
    main.c:368
    djmodule.c:323
    djauthinfo.c:925
    djauthinfo.c:1238


SOLUTION;

  $ killall lwsmd lwregd dcerpcd netlogond eventlogd lwiod lsassd

killall -9 if you have to.  We're going to reset state anyways.

  $ /bin/rm -rf /var/lib/likewise-open
  $ mkdir -p /var/lib/likewise-open/{db,rpc,run}
  $ chmod 700 -p /var/lib/likewise-open/db

Now start lwsmd:

  $ /etc/init.d/lwsmd start

Import settings

  $ for file in /etc/likewise-open/*.reg; do lwregshell import $file;
done

Reload lwsmd

   $ /etc/init.d/lwsmd reload

Start lsassd

  $ lwsm start lsass

You will have a clean state.  You should now be able to rejoin the
domain and hopefully everything will be resolved.

---

