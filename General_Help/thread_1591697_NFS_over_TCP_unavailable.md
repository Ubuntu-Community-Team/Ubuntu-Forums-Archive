---
title: "NFS over TCP unavailable"
date: 2010-10-09
forum: General Help
---

### Post by vader95 on 2010-10-09
Hi,

I followed this tutorial to boot a live CD off of a pxe server. [HTML]http://www.serenux.com/2010/05/howto-get-an-ubuntu-live-cd-to-boot-off-a-pxe-server/[/HTML]Whenever I go to boot off the network, I get this error ```
NFS over TCP not available from (IP address of server)
connect: Network is unreachable
connect: permission is denied.
```Does anybody have any information on this, I am using ubuntu 10.04.1 as the server.

Thanks in advance,

vader95

---

### Post by luvshines on 2010-10-09
You mean NFS over TCP is unavailable when you try to boot ??

Maybe you need to check on the server side:
```
rpcinfo -p localhost | egrep "mount|nfs|port"
```

If NFS is offering TCP connection or not

---

### Post by vader95 on 2010-10-09
Hi,

First of all, thank you for your reply.

Yes, NFS is not available when i try to boot via PXE.
When I ran that code you gave me I received 
```
    program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
```It appears to me that there is a connection, but i'm not too sure.

Thank you,
vader95

---

### Post by luvshines on 2010-10-10
Steps 3-6 in the link you posted explain how to setup NFS on any server and export the files. Did you follow those steps ?

---

### Post by vader95 on 2010-10-10
Yes I have done that.

Do you think that I should reinstall NFS and see if that works?

Thanks

---

### Post by luvshines on 2010-10-10
> **vader95 said:**
> Yes I have done that.

Do you think that I should reinstall NFS and see if that works?

Thanks

Try to start/restart NFS service on the server:
```
sudo /etc/init.d/nfs-kernel-server restart
```

---

### Post by SeijiSensei on 2010-10-10
Just checking, but is there a firewall between these machines?  Maybe it's set to only pass UDP for NFS and not TCP?

---

### Post by vader95 on 2010-10-10
Thank you for the replies.

I have tried restarting the nfs-kernel-server, but it still doesn't work.

No, there is no firewall between the two machines, that was going to be after the boot server was working.

vader95

---

### Post by luvshines on 2010-10-11
What did restart command say ??

---

### Post by vader95 on 2010-10-11
> **luvshines said:**
> What did restart command say ??

```

user@servername:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ]
 * Unexporting directories for NFS kernel daemon...                      [ OK ]
 * Exporting directories for NFS kernel daemon...                        [ OK ]
 * Starting NFS kernel daemon                                            [ OK ]

```

---

### Post by luvshines on 2010-10-11
> **vader95 said:**
> ```

user@servername:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ]
 * Unexporting directories for NFS kernel daemon...                      [ OK ]
 * Exporting directories for NFS kernel daemon...                        [ OK ]
 * Starting NFS kernel daemon                                            [ OK ]

```

Weird !! When it says OK, it should be running.

Just make sure if it is actually not running:
```
ps aux | egrep "nfs|mountd"
```

If it is not then check the exit status of restart command:
```
sudo /etc/init.d/nfs-kernel-server restart; echo $?
```

You can also opt for seeing actually what is happening behind the scenes:
```
sudo sh -x /etc/init.d/nfs-kernel-server restart
```

On my system it ends with something like:
```
+ /etc/init.d/nfs-kernel-server stop
 * Stopping NFS kernel daemon                                                                                                                                                          [ OK ] 
 * Unexporting directories for NFS kernel daemon...                                                                                                                                    [ OK ] 
+ sleep 1
+ /etc/init.d/nfs-kernel-server start
 * Exporting directories for NFS kernel daemon...                                                                                                                                      [ OK ] 
 * Starting NFS kernel daemon                                                                                                                                                          [ OK ] 
+ exit 0
```

---

### Post by vader95 on 2010-10-11
> **luvshines said:**
> Weird !! When it says OK, it should be running.

Just make sure if it is actually not running:
```
ps aux | egrep "nfs|mountd"
``````
ps aux | egrep "nfs|mountd"
root       636  0.0  0.0      0     0 ?        S    15:07   0:00 [nfsiod]
root       759  0.0  0.0      0     0 ?        S    15:07   0:00 [nfsd4]
root       760  0.0  0.0      0     0 ?        S    15:07   0:00 [nfsd]
root       761  0.0  0.0      0     0 ?        S    15:07   0:00 [nfsd]
root       762  0.0  0.0      0     0 ?        S    15:07   0:00 [nfsd]
root       763  0.0  0.0      0     0 ?        S    15:07   0:00 [nfsd]
root       764  0.0  0.0      0     0 ?        S    15:07   0:00 [nfsd]
root       765  0.0  0.0      0     0 ?        S    15:07   0:00 [nfsd]
root       766  0.0  0.0      0     0 ?        S    15:07   0:00 [nfsd]
root       767  0.0  0.0      0     0 ?        S    15:07   0:00 [nfsd]
root       771  0.0  0.1   2200   368 ?        Ss   15:07   0:00 /usr/sbin/rpc.mountd --manage-gids
allen     1309  0.0  0.3   3316   812 pts/0    S+   17:05   0:00 egrep --color=auto nfs|mountd

```> **luvshines said:**
> If it is not then check the exit status of restart command. You can also opt for seeing actually what is happening by:
```
sudo sh -x /etc/init.d/nfs-kernel-server restart
```
```
 sudo sh -x /etc/init.d/nfs-kernel-server restart
+ DESC=NFS kernel daemon
+ PREFIX=/usr
+ [ -x /usr/sbin/rpc.nfsd ]
+ [ -x /usr/sbin/rpc.mountd ]
+ [ -x /usr/sbin/exportfs ]
+ DEFAULTFILE=/etc/default/nfs-kernel-server
+ RPCNFSDCOUNT=8
+ RPCNFSDPRIORITY=0
+ RPCMOUNTDOPTS=
+ NEED_SVCGSSD=no
+ RPCSVCGSSDOPTS=
+ PROCNFSD_MOUNTPOINT=/proc/fs/nfsd
+ [ -f /etc/default/nfs-kernel-server ]
+ . /etc/default/nfs-kernel-server
+ RPCNFSDCOUNT=8
+ RPCNFSDPRIORITY=0
+ RPCMOUNTDOPTS=--manage-gids
+ NEED_SVCGSSD=
+ RPCSVCGSSDOPTS=
+ . /lib/lsb/init-functions
+ FANCYTTY=
+ [ -e /etc/lsb-base-logging.sh ]
+ . /etc/lsb-base-logging.sh
+ /etc/init.d/nfs-kernel-server stop
 * Stopping NFS kernel daemon                                            [ OK ]
 * Unexporting directories for NFS kernel daemon...                      [ OK ]
+ sleep 1
+ /etc/init.d/nfs-kernel-server start
 * Exporting directories for NFS kernel daemon...                        [ OK ]
 * Starting NFS kernel daemon                                            [ OK ]
+ exit 0

```

Here is the output, everything seems to be in order.  However, i was just thinking about this, could this not be working because I don't have a domain name set.  I have the DNS servers set, but no .local or .home?

Thank you,
vader95

---

### Post by luvshines on 2010-10-11
Something looks wrong. If it is running good then it should be listed in rpcinfo -p localhost

This is how I have it:
```
ps aux | egrep "nfs|mountd"
root      4022  0.0  0.0      0     0 ?        S    00:49   0:00 [nfsd4]
root      4023  0.0  0.0      0     0 ?        S    00:49   0:00 [nfsd]
root      4024  0.0  0.0      0     0 ?        S    00:49   0:00 [nfsd]
root      4025  0.0  0.0      0     0 ?        S    00:49   0:00 [nfsd]
root      4026  0.0  0.0      0     0 ?        S    00:49   0:00 [nfsd]
root      4027  0.0  0.0      0     0 ?        S    00:49   0:00 [nfsd]
root      4028  0.0  0.0      0     0 ?        S    00:49   0:00 [nfsd]
root      4029  0.0  0.0      0     0 ?        S    00:49   0:00 [nfsd]
root      4030  0.0  0.0      0     0 ?        S    00:49   0:00 [nfsd]
root      4034  0.0  0.0   2416   372 ?        Ss   00:49   0:00 /usr/sbin/rpc.mountd --manage-gids


scooby@scoob-laptop:~$ rpcinfo -p | egrep "nfs|mount|port"
program vers proto   port
100000    2   tcp    111  portmapper
100000    2   udp    111  portmapper
100003    2   udp   2049  nfs
100003    3   udp   2049  nfs
100003    4   udp   2049  nfs
100003    2   tcp   2049  nfs
100003    3   tcp   2049  nfs
100003    4   tcp   2049  nfs
100005    1   udp  34461  mountd
100005    1   tcp  38215  mountd
100005    2   udp  34461  mountd
100005    2   tcp  38215  mountd
100005    3   udp  34461  mountd
100005    3   tcp  38215  mountd

```

And if then I do 'nc' on 2049 port, it says success:
```

scoob@scooby-laptop:~$ nc -zv localhost 2049
nc: connect to localhost port 2049 (tcp) failed: Connection refused
Connection to localhost 2049 port [tcp/nfs] succeeded!
```

Don't think this will help, still try restarting portmap service:
```
sudo /etc/init.d/portmap restart
```

---

### Post by vader95 on 2010-10-11
here is what i show:

```
 rpcinfo -p | egrep "nfs|mount|port"
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  49158  mountd
    100005    1   tcp  55825  mountd
    100005    2   udp  49158  mountd
    100005    2   tcp  55825  mountd
    100005    3   udp  49158  mountd
    100005    3   tcp  55825  mountd
```

```
 rpcinfo -p localhost
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  53839  status
    100024    1   tcp  40287  status
    100021    1   udp  47511  nlockmgr
    100021    3   udp  47511  nlockmgr
    100021    4   udp  47511  nlockmgr
    100021    1   tcp  48347  nlockmgr
    100021    3   tcp  48347  nlockmgr
    100021    4   tcp  48347  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  49158  mountd
    100005    1   tcp  55825  mountd
    100005    2   udp  49158  mountd
    100005    2   tcp  55825  mountd
    100005    3   udp  49158  mountd
    100005    3   tcp  55825  mountd

```and
```
nc -zv localhost 2049
nc: connect to localhost port 2049 (tcp) failed: Connection refused
Connection to localhost 2049 port [tcp/nfs] succeeded!

```

---

### Post by luvshines on 2010-10-11
Is this after portmap restart ??

Just came across this:
[https://bugs.launchpad.net/ubuntu/lucid/+source/nfs-utils/+bug/540637](https://bugs.launchpad.net/ubuntu/lucid/+source/nfs-utils/+bug/540637)

Says same thing, stop/start portmap

Does the remote boot still complains of NFS unavailable over TCP ?

---

### Post by vader95 on 2010-10-11
to restart portmap should i use 
```
sudo /etc/init.d/portmap restart
```

---

### Post by luvshines on 2010-10-11
> **vader95 said:**
> to restart portmap should i use 
```
sudo /etc/init.d/portmap restart
```

I don't think that is required now, everything looks OK.

In you Comment #3 you posted only portmapper was shown in rpcinfo so I thought it is still that way :D

Does the original issue still exists ??

Are any firewalls in place ? If they are, maybe try switching them off
```
sudo service iptables status
```
If they are running
```
sudo service iptables stop
```

Similarly,
```

sudo ufw status
sudo ufw disable
```

---

### Post by vader95 on 2010-10-11
> **luvshines said:**
> I don't think that is required now, everything looks OK.

In you Comment #3 you posted only portmapper was shown in rpcinfo so I thought it is still that way :D

Does the original issue still exists ??

Are any firewalls in place ? If they are, maybe try switching them off
```
sudo service iptables status
```If they are running
```
sudo service iptables stop
```Similarly,
```

sudo ufw status
sudo ufw disable
```

iptables reports unrecognized service

ufw is inactive

---

### Post by luvshines on 2010-10-12
**Does remote boot still complain of unavaiable NFS over TCP ?**

---

### Post by vader95 on 2010-10-12
sorry, missed that in your last comment,

Yes it does still complain.

Is it possible my server is trying to get a username and password from the NFS client.  I have it set to no_root_squash, but maybe the server is trying to kick it out.

thank you,
vader95

---

### Post by luvshines on 2010-10-12
> **vader95 said:**
> sorry, missed that in your last comment,

Yes it does still complain.

Is it possible my server is trying to get a username and password from the NFS client.  I have it set to no_root_squash, but maybe the server is trying to kick it out.

thank you,
vader95

I don't think NFS protocols involve username/passwd mechanisms

Can you test this:
```
showmount -e <server-ip>
```

---

### Post by vader95 on 2010-10-12
this gives me```
showmount -e (ip)
Export list for (ip)
/srv/ubuntu-livecd/i386 *
```

---

### Post by luvshines on 2010-10-12
Phew !! Now I am totally stumped :mad:

Since we have checked everything on server side, it looks like the client side issue now

Can find lot of bug reports which ask to add 'udp' as mount option but since I don't have such an environment can't try it.

---

### Post by vader95 on 2010-10-12
> **luvshines said:**
> Phew !! Now I am totally stumped :mad:

Since we have checked everything on server side, it looks like the client side issue now

Can find lot of bug reports which ask to add 'udp' as mount option but since I don't have such an environment can't try it.

Well, I appreciate all your help either way. :)

I'm upgrading the server to 10.10 right now, and after that, i might try to find some configuration file and see if any settings are set incorrectly.


Thank you for all your help.

vader95

PS. If I find anything, I'll post it here and let you know.

---

### Post by vader95 on 2010-10-19
I finally got it working, i re-installed 10.04 and went through the configuration and it all works.  Must have been a configuration error somewhere???

I will be posting the procedure soon, once i get it all fixed up.

Thanks,
vader95

---

### Post by vader95 on 2010-10-21
[http://ubuntuforums.org/showthread.php?t=1517094](http://ubuntuforums.org/showthread.php?t=1517094)

Post with all the links.

---

### Post by Nutter on 2013-05-02
I also had this problem.  Turns out it was due to permissions.  The image I was trying to PXE boot from had too-restrictive permissions.

I realize this is really out-of-date but it is a top match on Google and this might help someone.

---

