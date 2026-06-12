---
title: "ssh script"
date: 2010-11-03
forum: General Help
---

### Post by ub007 on 2010-11-03
Hi,

I have scripted this code to ssh into my remote server and log back some info.

> import sys, os, re, optparse, traceback, types, time, getpass
import pexpect, pxssh
import readline, atexit

begin = time.time()
os.system('nc -l 2222 > log%s &' %begin)
time.sleep(50)
child = pexpect.spawn ('ssh david@192.168.0.14')
child.expect ('password:')
child.sendline ('mypass')
child.expect ('$')
child.sendline ('df |nc 192.168.0.14 2222')
child.sendline ('exit')
child.sendline ('exit')

However each time I get 0byte files logged.
eg
> 0 Nov  3 11:15 log1288782916.15

No when I do the same stuff manually:
local machine

> nc -l 2222 > log &

Then ssh into remote server & do
> df |nc 192.168.0.14 2222
it works 
> 2880 Nov  3 11:27 log

I do a strace on nc ( launched from script )
> shutdown(4, 0 /* receive */)            = -1 ENOTCONN (Transport endpoint is not connected)

Any thoughts guys?

Thanks in advance

David

---

### Post by DaithiF on 2010-11-03
why are you netcat'ing the df data to the servers ip rather than back to your client machine?
child.sendline ('df |nc **192.168.0.14** 2222')

192.168.0.14 is the address of the server, no?

---

### Post by ub007 on 2010-11-03
oopss, that was a typo. Thanks for poiting that out.

child.sendline ('df |nc 192.168.0.18 2222').

Back to my client machine

---

### Post by HermanAB on 2010-11-03
BTW, don't use expect to force a password into SSH, it is better to set up a key instead.

---

