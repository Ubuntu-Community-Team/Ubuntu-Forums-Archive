---
title: "rc.local doesn't execute at startup, I have to start it manually to make it work"
date: 2012-08-14
forum: General Help
---

### Post by Jimboland on 2012-08-14
I have two machines with ubuntu, both are using the same script, on my desktop its working like it should, and on my notebook it isn't.

When I do: sudo sh /etc/rc.local it works perfect! (mounting my nas)
But when I reboot my system, It wont start.

I changed owner to me, I changed permissions to 755 but its not working.

I tried changing my password, but now I have two passwords, apperently:confused:

My old password, which i have to enter at startup (unlock default keyring)

My sudo password, which I have to use for everything else:confused:

---

### Post by efflandt on 2012-08-15
Does it show proper file permissions to execute (755) and does everything in it have full paths (expect limited env):

$ **ls -l /etc/rc.local**
-rwxr-xr-x 1 root root 306 Apr 25 11:04 /etc/rc.local

---

### Post by Jimboland on 2012-08-15
Two times yes, that's why I don't understand. It should work.

Permissions:

[I]porquino@porquino-HP-G61-Notebook-PC:~$ sudo ls -l /etc/rc.local
-rwxr-xr-x 1 porquino porquino 427 Aug 14 23:12 /etc/rc.local[/I]

Script:

[I]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mount -t cifs //192.168.10.104/volume_1 /home/porquino/nas/ -o username=myusername,password=mypass,domain=workgroup

exit 0
[/I]

I'm using 12.04

---

### Post by spjackson on 2012-08-15
The ownership should be root:root. However, I don't think that having porquino:porquino will stop it working.

I notice that you have "domain=workgro  up" i.e. with a space before "up". I guess this is a mistake in your post, since you say that it works when run manually.

I suspect a timing issue. Although networking is started before rc.local  runs, networking may not yet be ready (e.g. waiting for an IP address  from DHCP).I suggest you add
```

>> /var/log/rc.local.log 2>&1

```to the end of your mount command, then examine the log after rebooting. This should give a clue about what's going wrong.

---

### Post by Jimboland on 2012-08-15
[I]mount error(101): Network is unreachable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)  [/I]

I'm guessing this is because my wireless network adaptor is not working when the script is executed.

So would it help if I enter something like:

Ping 192.168.10.104 -c 30

before the mount command, to  add a 'pause' so my laptop has time to activate the wireless adaptor?

I will give it a try and update my post.


Didn't work.

---

### Post by Jimboland on 2012-08-15
The solution:

I changed owner to root.

And before the mount command I added:

Sleep 2m

Then my script, and now its working!:D

So:

[B]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sleep 2m
mount -t cifs //192.168.10.104/volume_1 /home/porquino/nas/ -o username=myusername,password=mypass,domain=workgroup

exit 0[/B]

*edit: changing 2m (2 minutes) to 6 (6 seconds) also worked fine for me.*

Thanks for the tip spjackson! I was trying something simular like:

*>> /var/log/rc.local.log 2>&1 * 

with 

>> */home/porquino/rc.log *

But this always gave me empty files.

---

### Post by spjackson on 2012-08-15
> **Jimboland said:**
> 
Thanks for the tip spjackson! I was trying something simular like:

*>> /var/log/rc.local.log 2>&1 * 

with 

>> */home/porquino/rc.log *

But this always gave me empty files.
Great. I'm glad you got it working.

The 2>&1 is there to redirect the error messages (standard error). >> on its own just redirects normal output (standard output).

It may be possible to do something better than waiting 2 minutes. For nfs mounts, there is the bg option, which causes the mount to be retried in the background. cifs doesn't seem to have this. There's also _netdev but I don't think that results in automatic retries.

If it can't be solved via mount options (and I'm not sure whether it can or not), I'd be inclined to have a loop like this.
```

while [ /bin/true ]
do
    mount command goes here
    if [ $? -eq 0 ]; then
        break
    fi
    sleep 10
done &

```

---

### Post by Jimboland on 2012-08-15
> **spjackson said:**
> 
It may be possible to do something better than waiting 2 minutes. For nfs mounts, there is the bg option, which causes the mount to be retried in the background. cifs doesn't seem to have this. There's also _netdev but I don't think that results in automatic retries.

If it can't be solved via mount options (and I'm not sure whether it can or not), I'd be inclined to have a loop like this.
```

while [ /bin/true ]
do
    mount command goes here
    if [ $? -eq 0 ]; then
        break
    fi
    sleep 10
done &

```


I tried to do that but I can't mount nfs shares for some reason. I always get the message:

***mount.nfs: access denied by server while mounting 192.168.10.104:/mnt/HD/HD_a1/Data***

I installed nfs-common, started the nfs service on my nas but I'm not able to mount it with nfs. So I have to stick with cifs for now.

Its maybe a bit stange to use cifs in a Linux environment but its the only thing thats working for me.
smb4k, gvfs and pyneighborhood all gave me slow network speeds, cifs solved this for me. But sinds i'm only using Linux, its would be better to use nfs, I think.

Anyway, thanks for your help!

---

### Post by fabietto0102 on 2012-08-31
Hi, I've a very similar issue and hope you can help me please! 

I need to run 

```
sudo etc/init.d/networking restart
```

automatically at login, but how? 

I tried to add the line to rc.local but it doesn't work. From reading this thread, I suspect that I first need to be connected to the network, which I do using NetworkManager with a wifi connection. 

How can I write a while loop in shell that says "while I'm not connected, loop' please?

---

### Post by dcstar on 2012-09-01
> **Jimboland said:**
> I have two machines with ubuntu, both are using the same script, on my desktop its working like it should, and on my notebook it isn't.
.........

Probably because the networking on the Desktop is actually functional when you run your networking command in rc.local and the Notebook does not have functioning networking when it runs.

rc.local is not meant to mount network shares like that, that is what /etc/fstab is for.

---

### Post by Jimboland on 2012-12-07
> **dcstar said:**
> Probably because the networking on the Desktop is actually functional when you run your networking command in rc.local and the Notebook does not have functioning networking when it runs.

rc.local is not meant to mount network shares like that, that is what /etc/fstab is for.

Yes that was the problem, my wireless adaptor was not working at system start.

I noticed that in Ubuntu 12.10 the script doesn't work anymore, so I'm forced to use fstab now.

---

